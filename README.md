# README

# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
|--------------------|--------|---------------------------|
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| name               | string | null: false               |
| profile            | text   | null: false               |
| occupation         | text   | null: false               |
| position           | text   | null: false               |

### Association

- has_many :comments
- has_many :prototypes

## prototypes テーブル

| Column     | Type       | Options                        |
|------------|------------|--------------------------------|
| title      | string     | null: false                    |
| catch_copy | text       | null: false                    |
| concept    | text       | null: false                    |
| user       | references | null: false, foreign_key: true |

### Association

- has_many :comments
- belong_to :users

## comments テーブル

| Column    | Type      | Options                       |
|-----------|-----------|-------------------------------|
| content   | text      | null:false                    |
| prototype | reference | null:false, foreign_key: true |
| user      | reference | null:false, foreign_key: true |

### Association

- belong_to :users
- belong_to :prototypes