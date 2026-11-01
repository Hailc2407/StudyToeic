# StudyToeic: English Room

Phòng học tiếng Anh (TOEIC và Grammar) chạy trên GitHub Pages:
**https://hailc2407.github.io/StudyToeic/**

Lối vào khác: phím tắt **Ctrl + Shift + L** trên https://hailc2407.github.io/, hoặc link cũ
https://hailc2407.github.io/study/ (tự chuyển hướng sang đây, giữ cả phần `#…`).

## Cấu trúc

```
index.html, study.js, study.css   ứng dụng (không cần build)
vault.js                          đọc và giải mã vault/ trong trình duyệt
vault/                            bài học, ảnh, audio đã mã hoá AES-GCM (tên file không lộ nội dung)
assets/img/favicon.svg            biểu tượng trang
tools/vault.mjs                   mã hoá một thư mục nguồn vào vault/
tools/unvault.mjs                 giải mã vault/ ra thư mục nguồn
.claude/skills/english-room/      skill Claude Code: lên kế hoạch, soạn, test, phát hành bài học
```

Mật khẩu vault là `english`; `study.js` tự mở khoá nên người học không phải nhập.

## Soạn hoặc sửa bài

```bash
VAULT_PASSWORD=english node tools/unvault.mjs vault /tmp/vsrc   # lấy toàn bộ nguồn đã build
# … thêm/sửa lessons/<id>.json, img/<id>/ … (xem .claude/skills/english-room/)
VAULT_PASSWORD=english node tools/vault.mjs /tmp/vsrc vault     # mã hoá lại (nguồn phải đủ mọi bài)
```

Sách và audio gốc nằm trong repo riêng tư `Hailc2407/toeic-materials`.

## Chạy thử ở máy

```bash
mkdir -p /tmp/serve && ln -sfn "$PWD" /tmp/serve/StudyToeic
cd /tmp/serve && python3 -m http.server 8765    # rồi mở http://localhost:8765/StudyToeic/
```
