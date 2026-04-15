# RedteamWorkstation

这是一个为红队提供的团队协作多功能集成平台；
采用C/S架构，类似CobaltStrike；
将所有功能，分为client模块和server模块；
client这是只有本地可用，调用本地算里和内存；
server是像一些密码破解，等耗费性能的交由服务器，服务器主要提供信息存储和交换，用于队伍间沟通，和一些贡献模块；
我们要内置一些模块，其他的可以由别人添加/
client内置里面包含了许多模块如burp的Proxy，Repeater，Intruder。
server这是资产梳理，聊天，密码hash破解等。

# 核心理念
按照客户端/服务端的模块开发组装
除了核心模块 如 与服务器通讯等，都可以自动将模块内存卸载到硬盘，激活时加载，允许手动加载卸载，有任务时不允许，设置里允许选择；
要做的算是All in one，都是由mods 组成；
即使是核心模块 也和其他模块规范相同，只是标记上为核心，不可卸载。

## 技术栈
- 语言：Rust 1.94.x
- 客户端：Rust + gpui
- 服务器：Rust + actixweb + surrealdb

## 常用命令

### 代码检查
使用cargo自带即可

## 项目结构
- `src/client/` — 客户端代码
- `src/client/mods` — 客户端 自定义模块
- `src/client/schema.md` — 架构图 大纲 函数调用关系
- `src/sever/` — 服务端代码
- `src/sever/mods` — 服务端 自定义模块
- `src/sever/schema.md` — 架构图 大纲 路由，描述
- `tests/` — 测试文件，与 src/ 目录结构镜像对应

## 编码规范
- 使用cargo
- 所有函数上方简短说明
- 新增 API 路由必须同步添加测试

## 注意事项
- 添加新函数后务必先测试
- 合理将 数据 服务 路由 分层解耦，如果可以 采用合适的设计模式
- 每次开始操作前，将上次代码git commit， 内容由你进行 按照约定是提交规范来写
