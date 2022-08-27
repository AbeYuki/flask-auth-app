# flask-auth-app


# docker 開発環境構築
```
docker compose up -d --build
```
初回構築の場合、 DB 作成コマンド実行
```
docker exec flask_app python -c "
from project import db, create_app, models
db.create_all(app=create_app())"
```

# venv 開発環境構築(sqliteの場合)
```
python3 -m venv env
```
```
source env/bin/activate
```
```
pip install -r requirements.txt
```
```
export FLASK_APP=project
```
```
export FLASK_DEBUG=1
```
```
export FLASK_ENV=development
```

project/__init__.py のコメントアウトを編集
```
vim project/__init__.py
```
```py
def create_app():
    ``` ```
    app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///db.sqlite'
    #app.config['SQLALCHEMY_DATABASE_URI']  = 'mysql+pymysql://{user}:{password}@{host}/{database}?charset=utf8'.format(
    #  **{
    #    'user': os.getenv('MARIADB_USER'),
    #    'password': os.getenv('MARIADB_PASSWORD'),
    #    'host': os.getenv('DB_HOST'),
    #    'database': os.getenv('MARIADB_DATABASE'),
    #  })
    ``` ```
```

# create sqlite
```
python -c "
from project import db, create_app, models
db.create_all(app=create_app())"
```
