# Motion Spec Editor 使用 SOP

## 1. 目的

使用本地 `motion-spec-editor.html` 模板编辑动效 Spec，将结果同时保存到本地并同步至 GitHub，获得可公开预览的 GitHub Pages 地址，最后插入飞书文档供开发人员查看。

## 2. 核心流程

```text
打开本地模板 → 编辑 Spec → 保存并导出 → 选择本地保存位置
→ 上传 GitHub → 复制 Pages 地址 → 粘贴到飞书文档
```

## 3. 使用前准备（仅首次需要）

### 3.1 准备模板

保留一份未经项目数据修改的 `motion-spec-editor.html`，作为创建新动效 Spec 的模板。不要直接把模板覆盖为某个具体项目文件。

### 3.2 创建 GitHub Token

1. 登录 GitHub。
2. 进入 `Settings → Developer settings → Personal access tokens → Fine-grained tokens`。
3. 点击 `Generate new token`。
4. `Resource owner` 选择 `dreamyworm`。
5. `Repository access` 选择 `Only select repositories`，并选中 `motion-specs`。
6. 在 `Repository permissions` 中设置：

   ```text
   Contents → Read and write
   Pages → Read-only
   ```

7. 生成并复制以 `github_pat_` 开头的 Token。

Token 只在当前打开的页面会话中临时使用，不会被写入导出的 HTML。关闭页面后，下次上传需要重新输入。

## 4. 创建新的动效 Spec

### 步骤 1：打开模板

双击本地 `motion-spec-editor.html`，使用浏览器打开。

### 步骤 2：进入编辑状态

点击页面右上角的编辑图标。页面右上角将显示：

- `退出编辑`
- `保存并导出`

### 步骤 3：编辑 Spec

根据实际动效补充或修改：

- 动画标题
- 触发时机
- 元素及元素名称
- 属性及属性名称
- 属性初始值与结束值
- 分段开始时间、持续时间
- 曲线插值
- Demo 视频（可选）

编辑后检查时间轴中的分段位置、时长、数值和插值参数是否与设计一致。

### 步骤 4：保存并导出

1. 点击右上角 `保存并导出`。
2. 在系统保存窗口中选择本地文件夹。
3. 输入清晰、唯一的 HTML 文件名，例如：

   ```text
   登录页-卡片入场动效.html
   ```

4. 确认保存。

系统会先生成一份独立的本地 HTML，再使用相同文件名上传至 GitHub 仓库。

浏览器会记住上一次使用的保存文件夹。首次通常从系统“文稿/Documents”目录开始，之后再次保存会默认回到上一次保存位置。

### 步骤 5：输入 GitHub Token

首次上传时，在弹窗中粘贴 Fine-grained Personal Access Token，然后确认。

页面会依次显示：

- 正在连接 GitHub
- 正在编码
- 正在上传
- GitHub 已上传，Pages 发布中 · 已等待 X 秒
- Pages 已更新 · 用时 X 秒

### 步骤 6：复制 Pages 地址

GitHub Pages 确认构建完成后，页面会生成对应的 Pages 地址，并尝试自动复制到剪贴板。若等待超过 180 秒仍未确认，页面会返回地址并提示 Pages 状态待确认。

地址格式为：

```text
https://dreamyworm.github.io/motion-specs/文件名.html
```

如果文件名包含中文，地址中出现 `%E7%...` 等编码属于正常现象，应复制完整地址。

### 步骤 7：插入飞书文档

1. 打开需要交付的飞书文档。
2. 粘贴 GitHub Pages 地址。
3. 根据飞书提供的选项，将链接切换为合适的预览或嵌入展示方式。
4. 检查开发人员是否能正常打开页面，并测试查看交互。

飞书嵌入页面为只读模式，不显示编辑按钮。开发人员仍可使用元素筛选、时间轴缩放、视频播放、参数浮层和插值曲线文档跳转等查看交互。

如果 GitHub 侧内容已经更新，而飞书仍显示旧版本，可点击页面右上角的强制刷新图标 `↻`。该按钮会重新获取 GitHub Pages 上的最新 HTML。

## 5. 更新已有 Spec

1. 打开之前导出的项目 HTML，不要重新打开空白模板。
2. 点击编辑图标并修改内容。
3. 点击 `保存并导出`。
4. 在系统保存窗口中确认原文件名和保存位置。
5. 输入 GitHub Token（如果当前页面尚未输入过）。
6. 系统会更新 GitHub 中原路径对应的 HTML。
7. 等待页面提示 `Pages 已更新`。
8. Pages 地址保持不变，飞书文档中的原链接无需重新替换；返回飞书后点击 `↻` 强制刷新即可。

## 6. 文件命名建议

推荐格式：

```text
业务或页面-元素或场景-动效类型.html
```

示例：

```text
登录页-卡片-入场动效.html
搜索页-筛选面板-展开动效.html
支付结果页-成功图标-反馈动效.html
```

避免使用 `/ \ : * ? " < > |` 等文件名特殊字符。

## 7. 注意事项

- 模板用于创建新文件，已有项目应从其导出的 HTML 继续编辑。
- 保存时浏览器会要求确认本地位置，这是浏览器的安全机制，无法完全取消。
- 保存选择器会记住上一次保存文件夹，但该记录属于当前电脑和浏览器，换电脑后需要重新选择。
- 不要把 GitHub Token 发给他人、写入飞书文档或保存在 HTML 中。
- Demo 视频会内嵌到 HTML，视频越大，保存和 GitHub 上传越慢。
- 建议上传前压缩视频，并控制文件总体大小。
- GitHub 上传完成不等于 Pages 已发布；应等待页面明确提示 `Pages 已更新` 后再到飞书查看。
- 更新已有文件时应保持原文件名，否则可能产生新的 GitHub 文件和新的 Pages 地址。
- 飞书嵌入页面不提供编辑功能。需要修改时，应打开本地项目 HTML，或在浏览器中独立打开对应的 GitHub Pages 页面。
- 页面在非编辑模式下默认勾选并展示全部元素。
- 预设插值曲线可点击跳转到对应的飞书曲线文档；用户自定义曲线没有跳转链接。

## 8. 常见问题

### 点击保存后没有出现 Token 输入框

关闭旧页面，重新打开最新的本地 HTML，再尝试保存。

### 提示 `Bad credentials` 或 `401`

Token 无效、过期或复制不完整。重新生成 Token，并再次粘贴。

### 提示 `403` 或 `Resource not accessible`

检查 Token 是否选中了 `motion-specs` 仓库，并确认：

```text
Contents → Read and write
Pages → Read-only
```

### 本地已保存，但 GitHub 上传失败

本地 HTML 不受影响。检查网络和 Token 后，重新打开刚保存的项目 HTML，再次点击 `保存并导出`。

### Pages 地址打开后还是旧内容

先确认保存页面已经提示 `Pages 已更新`。如果飞书中仍显示旧内容，点击嵌入页面右上角的 `↻` 按钮重新获取；必要时再使用浏览器强制刷新。

### 提示 Token 无法读取 Pages 状态

进入 GitHub 的 Fine-grained Token 设置，将 `Pages` 权限改为 `Read-only`，并点击 `Update token`。

### 飞书嵌入页面没有编辑按钮

这是预期行为。飞书内嵌环境仅用于查看，避免 iframe 对拖动操作的干扰。请回到本地项目 HTML 中编辑。

### 飞书中只显示普通链接

确认粘贴的是 `dreamyworm.github.io` 开头的 Pages 地址，而不是 GitHub 仓库中的 `github.com/.../blob/...` 文件地址。

## 9. 交付检查清单

- [ ] 标题和触发时机填写完整
- [ ] 元素、属性名称清晰
- [ ] 分段开始时间和持续时间正确
- [ ] 初始值、结束值和插值曲线正确
- [ ] Demo 视频可正常播放（如有）
- [ ] 本地 HTML 已保存
- [ ] GitHub 上传成功
- [ ] 页面提示 Pages 已更新
- [ ] Pages 地址可正常打开
- [ ] 飞书内默认展示全部元素
- [ ] 飞书中的强制刷新按钮可用
- [ ] 飞书文档中的链接或预览可正常访问
