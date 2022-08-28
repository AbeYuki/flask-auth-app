# flask-auth-app


# docker 開発環境構築( mariadb を利用)
```
docker compose up -d --build
```
初回構築の場合、 DB 作成コマンド実行
```
docker exec flask_app python -c "
from project import db, create_app, models
db.create_all(app=create_app())"
```

# venv 開発環境構築( sqlite を利用)
```
python3 -m venv env
```
仮想環境の作成  
```
source env/bin/activate
```
```
pip install -r requirements.txt
```
ファイルから環境変数を設定  
```
for i in $(cat app.env);do export $i ;done
```
project/\_\_init\_\_.py のコメントアウトを編集し、 URI を sqlite へ変更
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
db.sqlite を削除し sqlite を再構築する場合は DB 作成コマンド実行  
※ 本 repositry では sqlite を初回構築済みのため、そのまま使用する場合はコマンドの実行不要  
```
python -c "
from project import db, create_app, models
db.create_all(app=create_app())"
```
```
flask run
```
仮想環境を無効化する場合  
```
deactivate
```