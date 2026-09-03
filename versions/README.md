# Skill versions

Bản lưu của `plugins/amz-image-prompts/skills/amz-scene-creator/SKILL.md`.

| File | Version | Ghi chú |
|---|---|---|
| `v1.0-SKILL.md` | 1.0 (tag `v1.0`) | Trừu tượng hoá ref: xoá graphic device, dựng phòng Mỹ chung chung thay vì chép ref. |
| `v2.0-SKILL.md` | 2.0 (tag `v2.0`) | Ref điều khiển bối cảnh, ánh sáng và graphic device. Identity lock còn yếu với model tái tạo. |
| *(file đang chạy)* | 2.1 (tag `v2.1`) | Thêm structural lock. |

## Quay về bản cũ

```
git checkout v2.0 -- plugins/amz-image-prompts/skills/amz-scene-creator/SKILL.md
git commit -m "Roll back skill to v2.0"
```

Hoặc chép tay:

```
copy versions\v2.0-SKILL.md plugins\amz-image-prompts\skills\amz-scene-creator\SKILL.md
```

Nhớ hạ luôn `version` trong `plugins/amz-image-prompts/.codex-plugin/plugin.json`
cho khớp, rồi xoá marketplace trong Codex và thêm lại.
