# Product demo media / 产品演示素材

This folder is reserved for **real** product screenshots and a screen recording. The media has not been added yet. Please do not commit a mock video or empty image pretending to show a working feature.

本目录用于后续上传**真实**的小程序截图和操作录屏。目前只有占位目录和操作说明，没有实际展示视频或截图。

## Suggested screenshot files / 截图建议

Save PNG or WebP screenshots into [screenshots/](screenshots/) using these filenames:

| File | What to capture / 拍摄内容 |
| --- | --- |
| `01-home.png` | Home/navigation / 首页与入口 |
| `02-image-to-pattern.png` | Image → grid / 图片生成图纸 |
| `03-editor.png` | Editing + progress / 编辑和进度 |
| `04-inventory.png` | Stock view / 库存列表 |
| `05-inventory-log.png` | Stock changes / 库存流水 |

Only upload screenshots of features that really work in your test environment. You can omit or change filenames, but update the README links accordingly.

仅上传已运行的真实界面。可以少于五张，也可以修改文件名，但之后 README 的链接需要对应修改。

## Video slot / 录屏位置

- Reserved folder: [demo/](demo/)
- Suggested local filename: `pindou-walkthrough.mp4`
- Suggested sequence: home → image conversion → editing/progress → inventory change → saved pattern (roughly 60–90 seconds).

A compact GIF preview can live here too, but uploading large MP4 files into the ordinary Git history is discouraged. A GitHub Release attachment or public video host can be linked from the main README instead. If the video is hosted externally, no video file is required in this folder.

已经预留 `assets/demo/`。可录制 60–90 秒的首页 → 制作图纸 → 编辑与进度 → 库存变化 → 图纸库。体积较大的 MP4 不建议直接提交到 Git 历史；可以把视频作为 GitHub Release 附件或放到允许公开观看的平台，再在 README 放链接。GIF 小预览可视实际体积放到仓库。

## How to upload later / 之后如何上传

1. Open this public repository on GitHub and navigate to `assets/screenshots` or `assets/demo`.
2. Choose **Add file → Upload files**, select the actual files, and commit the upload.
3. Once media exists, update both `README.md` and `README.zh-CN.md`: replace “coming soon / 待上传” with real image embeds and a video link.
4. Check the links in an **incognito browser** so a recruiter who is not signed in can open them.

1. 进入公开仓库对应目录，点 **Add file → Upload files** 上传。
2. 提交图片/视频后，再把英文及中文 README 中的“待上传”替换成真实的图片嵌入和视频链接。
3. 使用浏览器无痕窗口确认无需登录也能查看；不要把只在微信内部或私有仓库中可见的链接当作公开 Demo。

## Privacy / 隐私检查

- Use a test account and sample patterns; hide WeChat IDs, personal avatars, chat notifications, API tokens, request headers, dashboard credentials and identifying user content.
- Make sure the video actually shows the app, not only slides or architecture diagrams.
- Never upload real database exports or secret configuration.

请用测试账号和非敏感图纸，隐藏微信号、个人头像、通知、API Token、请求头、管理后台凭据等信息；不要上传真实数据库或部署密钥。
