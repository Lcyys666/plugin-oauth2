# plugin-oauth2

Halo 2.0 的 OAuth2 第三方登录插件。

## 使用方法

1. 在 [Releases](https://github.com/Lcyys666/plugin-oauth2/releases) 下载最新的 JAR 文件。
2. 在 Halo 后台的插件管理上传 JAR 文件进行安装。
3. 进入 Console 端的用户管理，点击右上角的 `认证方式` 按钮进入认证方式管理列表即可看到当前插件提供的认证方式。
4. 按照下方的配置指南配置所需的认证方式并启用。
5. 进入当前登录用户的个人资料页面，即可绑定已启用的认证方式。

## 配置指南

目前支持的认证方式：

| 服务商 | 文档                                                                                                                                                   | Halo 所需配置               | Scope        | 回调地址                              |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------- | ------------ | ------------------------------------- |
| GitHub | [https://docs.github.com](https://docs.github.com/en/apps/oauth-apps/building-oauth-apps/creating-an-oauth-app)                                        | `Client ID` `Client Secret` | 无需手动设置 | `<SITE_URL>/login/oauth2/code/github` |
| GitLab | [https://docs.gitlab.com](https://docs.gitlab.com/ee/integration/oauth_provider.html#configure-gitlab-as-an-oauth-20-authentication-identity-provider) | `Client ID` `Client Secret` | `read_user`  | `<SITE_URL>/login/oauth2/code/gitlab` |
| Gitee  | <https://gitee.com/oauth/applications>                                                                                                                 | `Client ID` `Client Secret` | `user_info`  | `<SITE_URL>/login/oauth2/code/gitee`  |
| 微信 | [https://open.weixin.qq.com](https://open.weixin.qq.com) | `Client ID` `Client Secret` | `snsapi_login` | `<SITE_URL>/login/oauth2/code/wechat` |
| QQ | [https://graph.qq.com](https://graph.qq.com) | `Client ID` `Client Secret` | `get_user_info` | `<SITE_URL>/login/oauth2/code/qq` |
| 百度 | [https://openapi.baidu.com](https://openapi.baidu.com) | `Client ID` `Client Secret` | `basic` | `<SITE_URL>/login/oauth2/code/baidu` |
| 阿里云 | [https://www.aliyun.com](https://www.aliyun.com) | `Client ID` `Client Secret` | `user:read` | `<SITE_URL>/login/oauth2/code/aliyun` |

注意事项：

1. 如果认证失败，回调地址请使用 `http` 尝试。
2. <SITE_URL> 是不包含 `console` 的。
3. 如果你用于部署的服务器无法访问 GitHub，那 GitHub 认证会失败，其它同理，请先确认连通性。
4. 微信、QQ、百度和阿里云登录未经测试，有问题不负责。

## 开发环境

插件开发的详细文档请查阅：<https://docs.halo.run/developer-guide/plugin/hello-world>

```bash
git clone git@github.com:halo-sigs/plugin-oauth2.git

# 或者当你 fork 之后

git clone git@github.com:{your_github_id}/plugin-oauth2.git
```

```bash
cd path/to/plugin-oauth2
```

```bash
# macOS / Linux
./gradlew build

# Windows
./gradlew.bat build
```

修改 Halo 配置文件：

```yaml
halo:
  plugin:
    runtime-mode: development
    fixedPluginPath:
      - "/path/to/plugin-oauth2"
```
