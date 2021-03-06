{% tip %}

**提示**：
- 如果启用了必需的审查，并且对仓库具有_写入_、_管理员_或_所有者_访问权限的协作者提交请求更改的审查，则在同一协作者提交另一次要求批准拉取请求中更改的审查之前，拉请求不能合并。
- 即使没有获得批准审查，或者请求更改的审查者离开了组织或者联系不上，仓库所有者和管理员也可合并拉取请求。
- 如果同时启用了必需审查和过期审查，并且代码修改提交已推送到批准的拉取请求分支，则批准将予驳回。 拉取请求必须经过再次审查和批准才可合并。
- 当多个打开的拉取请求时分别有指向同一提交的头部分支时，如果一个或两者有待定或被拒绝的审查，您将无法合并它们。
- If your repository requires approving reviews from people with write or admin permissions, then any approvals from people with these permissions are denoted with a green check mark, and approvals from people without these permissions have a gray check mark. Approvals with a gray check mark do not affect whether the pull request can be merged.
- 拉取请求作者无法批准自己的拉取请求。

{% endtip %}
