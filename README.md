# flask-auth-app

# venv 開発環境構築
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
FLASK_ENV=development
```

# docker 開発環境構築
```
docker compose build --no-cache
```
```
docker compose up -d
```

# create sqlite
python -c "
from project import db, create_app, models
db.create_all(app=create_app())"