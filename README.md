# accounts.spacegt.com
用于 SSO  (基于 iframe 和 postMessage 的静默登录)

用户无感知：认证过程在后台通过隐藏的 iframe 完成，用户无需看到页面跳转。

更好的 SPA 体验：与单页应用完美结合，不会打断用户在应用中的操作流程。

避免回调URL注册：业务应用通常不需要在认证中心注册复杂的重定向回调URL（只需要一个用于 iframe 嵌入的静默认证页面）。

JWT 的无状态性：JWT 本身是无状态的，验证只依赖于密钥，符合 RESTful API 设计，方便后端服务验证。

克服第三方 Cookie 限制：postMessage 不依赖于 Cookie，而是基于消息传递，所以不受第三方 Cookie 禁用策略的影响。
