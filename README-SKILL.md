# Cài đặt BPMN skills & c8ctl (Cursor) — hasaki-research-notes

Hướng dẫn cài **hai skill BPMN** và CLI **c8ctl** trong repo này để agent Cursor tạo / sửa / lint file `.bpmn`.

---

## Đã cài trong repo này

| Thành phần | Nguồn | Vị trí / lệnh |
|------------|--------|----------------|
| Skill `bpmn` | [architawr/claude-bpmn-skill](https://github.com/architawr/claude-bpmn-skill) | `.agents/skills/bpmn/` |
| Skill `camunda-bpmn` | [camunda/skills](https://github.com/camunda/skills) — chỉ `camunda-bpmn` | `.agents/skills/camunda-bpmn/` |
| Khóa phiên bản skill | `skills-lock.json` (gốc repo) | dùng `npx skills experimental_install` để khôi phục |
| CLI `c8ctl` | npm `@camunda8/cli` | máy local (global), kiểm tra: `c8ctl --version` |

Cursor nhận skill qua chuẩn [Agent Skills](https://agentskills.io): canonical path là `.agents/skills/<tên>/SKILL.md` (installer ghi “copy → Cursor”).

---

## Yêu cầu môi trường

- Node.js ≥ 18 và npm  
- Mạng để clone GitHub lần đầu (`npx skills add …`)  
- Với skill `bpmn`: chạy thêm `npm install` trong thư mục skill (lấy `bpmn-moddle`, `bpmn-auto-layout`)  
- Với skill `camunda-bpmn`: cần **c8ctl ≥ 3.2.0** để `c8ctl bpmn lint` / `c8ctl bpmn format`

---

## 1. Cài skill (project-scoped, trong thư mục repo)

Mở terminal tại gốc `hasaki-research-notes`:

```bash
# Skill đọc/sửa BPMN 2.0 (layout + validate + lint control-flow)
npx skills add architawr/claude-bpmn-skill -y

# Skill Camunda BPMN (chỉ camunda-bpmn)
npx skills add camunda/skills@camunda-bpmn -y
```

Chỉ cài cho Cursor (không copy sang agent khác):

```bash
npx skills add architawr/claude-bpmn-skill -a cursor -y --copy
npx skills add camunda/skills@camunda-bpmn -a cursor -y --copy
```

Kiểm tra:

```bash
npx skills list
```

Kỳ vọng thấy `bpmn` và `camunda-bpmn` gắn agent **Cursor**.

### Dependencies của skill `bpmn` (một lần / mỗi máy)

```bash
npm install --prefix .agents/skills/bpmn
```

### Khôi phục từ khóa đã commit

```bash
npx skills experimental_install
```

---

## 2. Cài c8ctl (≥ 3.2.0)

Skill `camunda-bpmn` dùng `c8ctl bpmn lint` / `format`. Cài global:

```bash
npm install -g @camunda8/cli@^3.2.0
c8ctl --version
```

Ví dụ đã xác nhận trên máy: `c8ctl v3.3.0`.

Lệnh hay dùng:

```bash
c8ctl bpmn lint path/to/file.bpmn
c8ctl bpmn format -i path/to/file.bpmn
```

> Đồ án ưu tiên sơ đồ **nghiệp vụ** (`isExecutable="false"`, làn vai trò, nhãn XOR tiếng Việt). `c8ctl bpmn lint` kỳ vọng FEEL + DI lane kiểu Camunda 8 — có thể báo lỗi trên file đồ án dù skill `bpmn` validate/lint đã sạch. Khi nộp bài: mở Camunda Modeler / bpmn.io, bám [core_bpmn.md](./03-core/core_bpmn.md). Dùng `c8ctl bpmn format` khi cần chuẩn hóa XML.

---

## 3. Dùng skill trong Cursor

1. Mở workspace đúng thư mục `hasaki-research-notes` (có `.agents/skills`).  
2. Agent tự gọi skill khi bạn mở / nhờ tạo / sửa `.bpmn`, hoặc hỏi mô hình hóa quy trình.  
3. Có thể nhắc rõ: *dùng skill bpmn* hoặc *dùng camunda-bpmn + c8ctl lint*.

Công cụ kèm skill `bpmn` (sau khi `npm install`):

```bash
node .agents/skills/bpmn/scripts/bpmn-tool.mjs summarize path/to/file.bpmn
node .agents/skills/bpmn/scripts/bpmn-tool.mjs layout path/to/file.bpmn --rebuild
node .agents/skills/bpmn/scripts/bpmn-tool.mjs validate path/to/file.bpmn
node .agents/skills/bpmn/scripts/bpmn-tool.mjs lint path/to/file.bpmn
```

---

## 4. Cập nhật / gỡ skill

```bash
npx skills update -y
npx skills remove bpmn -y
npx skills remove camunda-bpmn -y
```

---

## 5. Liên kết đồ án

- Nguyên tắc làm việc: [README.md](./README.md)  
- Hướng dẫn vẽ B2/B4: [03-core/core_bpmn.md](./03-core/core_bpmn.md)  
- Gói Return-to-Resolve (B4): [03-core/return-to-resolve/](./03-core/return-to-resolve/)

---

## Ghi chú

- Skill cài **theo project** (trong repo), không bắt buộc cài global (`-g`).  
- Không commit `node_modules` của skill nếu nhóm thống nhất ignore; hiện `.agents/skills/bpmn/node_modules` sinh local sau `npm install`.  
- Nguồn skill bên thứ ba: luôn rà `SKILL.md` trước khi chạy lệnh hệ thống mà skill đề xuất.
