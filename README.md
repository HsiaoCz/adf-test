# adf-test

## 1、go-admin

是一个中后台应用框架，基于（gin, gorm, Casbin, Vue, Element UI）实现

基于 Casbin 的 RBAC 访问控制模型

坏 这里需要先学 Casbin RBAC 权限控制

Casbin 的PERM模型

P: Policy 策略 p={sub,obj,eft}  策略一般存储到数据库 因为一般会有很多

M: Matchers 匹配规则 Request和Policy的匹配规则
   m=r.sub == p.sub && r.act == p.act && r.obj == p.obj
   r 请求 p 策略
   这时候会把r和p按照上述描述进行匹配 从而返回匹配结果(eft) 如果不定义 会返回allow
   会返回allow 如果定义过了，会返回我们定义过的那个结果

E: Effect 影响 它决定我们是否可以执行
   e=some(where(p.eft==allow)) 这种情况下我们的一个matchers匹配完成 得到了allow 那么这条请求将被执行
   e=some(where(p.eft==allow))&&!some(where(p.eft==deny))
   这里的规则是定死的

Request 请求r={sub,obj,act}

role_definition 角色域

