# gdirect OAuth Branding 网站（个人使用版）

本压缩包是一套可以直接上传到静态网站托管平台的英文页面，用于描述**你自己配置的 gdirect OAuth Client**，不是原作者的官方网站。

## 包含文件

- `index.html`：Application home page（主页）
- `privacy.html`：Privacy policy（隐私政策）
- `terms.html`：Terms of service（服务条款）
- `styles.css`：页面样式
- `.nojekyll`：GitHub Pages 静态发布辅助文件
- `README_CN.md`：本说明

## 先核对公开信息

- 应用名：`gdirect`
- 联系邮箱：`leeechsh@gmail.com`（截图中提供；**部署后会公开显示**，不希望公开请批量替换）
- 用途：自己使用的桌面 OAuth Client，连接开源 gdirect
- 授权范围：`https://www.googleapis.com/auth/drive`（可对文件执行读写删除）
- 隐私政策内容基于 upstream README，提及本机 SQLite 凭据存储、下载文件及挂载缓存

**发布前请根据自己实际使用方式审核页面内容。** 如果你修改过程序，加入代理服务、数据上传、统计或多人使用，隐私披露也必须对应调整。

## GitHub Pages 快速部署

1. 登录 GitHub，新建一个 **Public** 仓库，例如 `gdirect-oauth-site`。
2. 将上述网页文件上传到仓库**根目录**，确保 `index.html` 位于根目录。
3. 打开 **Settings → Pages → Build and deployment**，选择 `Deploy from a branch`，Branch 选 `main`，Folder 选 `/ (root)`，保存。
4. 若 Github 用户名为 `<USERNAME>`，默认页面地址通常为：
   - 首页：`https://<USERNAME>.github.io/gdirect-oauth-site/`
   - 隐私政策：`https://<USERNAME>.github.io/gdirect-oauth-site/privacy.html`
   - 服务条款：`https://<USERNAME>.github.io/gdirect-oauth-site/terms.html`
5. 访问并检查三个链接均能直接打开，首页的 Privacy / Terms 链接也正常。

**重要：Google OAuth 官方发布/品牌验证要求验证域名所有权。** 只用共享的 `github.io` 域名，有可能无法满足 Google 对“自有且已验证域名”的要求；不能把 `github.com` 或上游作者的仓库域名当成你拥有的域名。为了最大限度避免认证失败，推荐将 GitHub Pages 绑定到你自己购买/控制的域名。

## 推荐：绑定自有域名

假设你真正拥有 `example.com`（仅为示例）：

1. 通过域名 DNS 平台将 `gdirect.example.com` 设置 CNAME 至 `<USERNAME>.github.io`（这里绝对不要带仓库路径）。
2. 在 Github 仓库 Settings → Pages → Custom domain 填 `gdirect.example.com`，按照官方指引确保 HTTPS 可用。
3. 在 Google Search Console 使用与你 Google Cloud 项目关联的 Owner/Editor 账号，验证 `example.com` 所有权。OAuth 验证通常要求 DNS 级 Domain property 验证。
4. Branding 中填写：
   - Application home page: `https://gdirect.example.com/`
   - Application privacy policy link: `https://gdirect.example.com/privacy.html`
   - Application terms of service link: `https://gdirect.example.com/terms.html`
   - Authorized domains: `example.com`
5. App name 设 `gdirect`，Support email 及 Developer contact email 使用你能接收邮件的真实邮箱。
6. 点击 Save，返回 Audience 刷新，再检查 `Publish app` 是否可点。

不要把 `example.com` 字样原样填写到 Google Cloud，它只是占位符。

## 注意事项

- 上述部署**只创建网页文件**，没有为你注册域名、发布网站或验证域名，也无法保证一定触发按钮解锁。
- 主页和隐私政策必须公开，无登录墙，且政策中对使用 Google 用户数据的描述必须与实际行为一致。
- `Publish app / In production` 与 Google 的品牌验证、敏感/受限范围验证**不是同一件事**；完整 Drive 权限可能产生额外验证要求。
- 不要把 `client_secret.json`、SQLite 数据库、access token、refresh token 或 Google Drive 文件上传到公开 GitHub 仓库。
- 如果只给自己用，也可以留在 Testing，并将账号加到 Test users；缺点是测试应用 refresh token 可能约 7 天失效。

资料：
- https://github.com/mizorewww/gdirect
- https://github.com/mizorewww/gdirect/blob/main/docs/configuration/google-cloud.md
- https://developers.google.com/identity/protocols/oauth2/production-readiness/brand-verification
- https://support.google.com/cloud/answer/13464321?hl=en
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
