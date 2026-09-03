# amz-scene-prompt

Codex/ChatGPT plugin marketplace chứa các skill viết prompt tạo ảnh sản phẩm cho Amazon và TikTok Shop.

## Cấu trúc

```
.agents/plugins/marketplace.json          <- Codex đọc file này đầu tiên
plugins/
  amz-image-prompts/
    .codex-plugin/plugin.json             <- tên, version, metadata của plugin
    skills/
      amz-scene-creator/SKILL.md          <- skill ảnh bối cảnh (lifestyle)
versions/                                 <- bản lưu các version skill cũ
CHANGELOG.md
```

Codex tự quét mọi `skills/<ten-skill>/SKILL.md`. Thêm skill mới = tạo thêm một thư mục
trong `skills/`, không cần khai báo ở đâu khác.

## Cài vào ChatGPT

Plugin > Thêm chợ plugin:

| Ô | Điền |
|---|---|
| Nguồn | `https://github.com/tduc4747/amz-scene-prompt.git` |
| Tham chiếu Git | `main` |
| Đường dẫn rút gọn | *để trống* |

Ô thứ ba là sparse checkout. Điền vào đó sẽ làm Codex không tải được
`.agents/plugins/marketplace.json` và marketplace hỏng. Luôn để trống.

Đang sửa tới lui thì dùng thư mục máy thay cho URL, khỏi push:
`D:\z. Other File\amz-plugin-repo\repo`, hai ô còn lại để trống.

## Quy trình cập nhật

`main` là bản đang chạy thật, không sửa trực tiếp. Mọi thay đổi làm trên nhánh khác.

```
git checkout -b dev            # hoặc v2.2, fix-lighting, ...
# sửa file
git commit -am "..."
git push -u origin dev
```

Test nhánh `dev`: xoá marketplace trong Codex, thêm lại với Tham chiếu Git = `dev`.

Chạy ổn thì đưa lên main và đánh tag:

```
git checkout main
git merge dev
git tag v2.2
git push && git push --tags
```

Rồi trong Codex đổi marketplace về `main`.

## Kiểm tra Codex đang chạy version nào

Ba dấu hiệu, phải khớp nhau:

1. Trang plugin, mục **Phiên bản** — lấy từ `plugin.json`
2. Dòng mô tả ngắn trên trang đó kết thúc bằng `— skill vX.Y`
3. Nhắn cho plugin đúng hai chữ `skill version`, nó trả về một dòng `amz-scene-creator vX.Y`

Lệch nhau = Codex đang dùng snapshot cache cũ. Xoá **marketplace** (không phải plugin)
rồi thêm lại, hoặc `codex plugin marketplace upgrade amz-plugins`.

## Quay về version cũ

```
git checkout v2.0 -- plugins/amz-image-prompts/skills/amz-scene-creator/SKILL.md
```

Hoặc chép tay từ `versions/`. Xem `versions/README.md`.
