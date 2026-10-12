

# Task7#

这一期你得了解一下fastapi的学习了，这大概率是你第一个接触的web框架



**什么是 FastAPI？**

在众多 Python 框架（如 Django, Flask）中，FastAPI 是近年来崛起最快的，原因只有三个：

1. **快 (Fast)**：基于现代 Python 的异步特性，性能可以和 NodeJS、Go 语言媲美。
2. **极简 (Easy)**：代码极其精简，写接口就像写普通函数一样自然。
3. **自带文档 (Auto-docs)**：**这是最惊艳的特性！** 你写完代码的瞬间，它会自动给你生成一个漂亮且可以直接测试的交互式网页 API 文档。

要使用 FastAPI，我们需要安装两个东西：框架本身，以及一个负责运行它的服务器

打开你的终端（Terminal/CMD），输入以下命令：

~~~
pip install fastapi
pip install "uvicorn[standard]"
~~~

*`fastapi` 是我们写逻辑的框架；`uvicorn` 是一个高性能的 ASGI 服务器，它负责把用户的 HTTP 请求接收进来，然后交给 FastAPI 去处理。*

新建一个文件，命名为 `main.py`，然后敲下这 5 行代码：

~~~python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "🎓 欢迎来到 FastAPI 的世界！"}
~~~

在终端中输入

~~~
uvicorn main:app --reload
~~~

`main`：你的文件名 `main.py`。

`app`：代码里 `app = FastAPI()` 这个变量名。

`--reload`：热更新魔法！你只要保存代码，服务器就会自动重启，不用每次手动关掉再开。



写后端接口，本质上就是处理“客户端传来的数据”。FastAPI 提供了三种最常用的传参方式：

1.  路径参数 (Path Parameters) - 获取特定资源

   ~~~python
   @app.get("/users/{user_id}")
   def get_user(user_id: int):
       # FastAPI 会自动把 user_id 转换成整数类型！
       return {"user": f"这是编号为 {user_id} 的用户档案"}
   ~~~

   ​

2.  查询参数 (Query Parameters) - 过滤和搜索

   ~~~python
   @app.get("/search")
   def search_item(keyword: str, page: int = 1):
       return {"搜索关键词": keyword, "当前页码": page}
   ~~~

   ​

3. 请求体与数据校验 (Request Body & Pydantic)

~~~python
from pydantic import BaseModel

# 定义一个类似于面向对象中的“类”，明确规定需要什么数据
class UserRegister(BaseModel):
    username: str
    password: str
    age: int  # 如果前端传来 "abc"，FastAPI 会自动拦截并报错，根本不需要你写 try...except！

@app.post("/register")
def register(user: UserRegister):
    # 只要代码能走到这里，说明 user 数据绝对是完美符合上面规则的
    return {
        "提示": "注册成功！",
        "用户名": user.username,
        "年龄": user.age
    }
~~~

`任务也很简单`

## 题目##

社团需要一个极简的“云留言板”，让新同学们可以打招呼。

你需要用 FastAPI 写两个接口，一个用来**看留言**，一个用来**发留言**。

1. **定义数据格式 (Pydantic)**：
   - 创建一个 `NewMessage` 类，规定发留言时必须提交两个信息：`name` (名字，字符串) 和 `text` (留言内容，字符串)。
2. **写留言接口 (POST)**：
   - 路由：`/send`
   - 接收用户传来的 `NewMessage` 数据，并把它存进一个全局的列表（List）里。
3. **看留言接口 (GET)**：
   - 路由：`/messages`
   - 把列表里所有的留言直接返回给前端。







