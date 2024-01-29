# README

## 手順

1. `docker compose -f compose-dev.yml run --rm web rails new . --force --no-deps --database=mysql`
2. `docker compose -f .\compose-dev.yml build`
3. yaml修正
```yaml
# database.yml
default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: <%= ENV.fetch("DATABASE_PASSWORD") %> #修正
  host: db #修正
  port: 3306 #修正
```
4. `docker compose -f compose-dev.yaml up -d`
5. `docker compose exec web rake db:create`

## 関連リンク

https://zenn.dev/peishim/articles/89bfa48396c348

https://zenn.dev/yoiyoicho/articles/90e1ea64772ea8

https://railsguides.jp/7_1_release_notes.html#%E6%96%B0%E8%A6%8Frails%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%A7dockerfile%E3%81%8C%E7%94%9F%E6%88%90%E3%81%95%E3%82%8C%E3%82%8B%E3%82%88%E3%81%86%E3%81%AB%E3%81%AA%E3%81%A3%E3%81%9F
