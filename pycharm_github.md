# pycharm + github

## 安装git
https://git-scm.com/downloads


## pycharm
### 1、配置Pycharm

### 2、下载github项目
VCS → Checkout from Version Control → Git

### 3、出现：Microsoft Visual C++ 14.0 is required 的解决方案


# 项目访问数据库方式
使用Flask-SQLAlchemy。创建 Flask 应用，选择加载配置接着创建 SQLAlchemy 对象时候把 Flask 应用传递给它作为参数。
```
app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql://root:root123@localhost:3306/test'
app.config['SQLALCHEMY_COMMIT_ON_TEARDOWN'] = True
db = SQLAlchemy(app)
```
一旦创建，这个对象就包含 sqlalchemy 和 sqlalchemy.orm 中的所有函数和助手。此外它还提供一个名为 Model 的类，用于作为声明模型时的 delarative 基类:
```
from server import db

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True)
    email = db.Column(db.String(120), unique=True)

    def __init__(self, username, email):
        self.username = username
        self.email = email

    def __repr__(self):
        return '<User %r>' % self.username
```
为了创建初始数据库，只需要从交互式 Python shell 中导入 db 对象并且调用 SQLAlchemy.create_all() 方法来创建表和数据库:
```
db.create_all()
```
增删改查
```
admin = User('admin', 'admin@example.com')
db.session.add(admin)
db.session.commit()

users = User.query.all()
admin = User.query.filter_by(username='admin').first()
```


# 访问redis的方法


