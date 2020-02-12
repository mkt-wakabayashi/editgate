# version

ruby 2.5.1
Rails 5.2.3

# DB設計 

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|image|string|
|nickname|string|null: false,index: true|
|mail|string|null: false, unipue: true|

### Association
- has_many :articles
- has_many :comments
- has_many :likes
- has_many :groups, through: :group_users
- has_many :group_users

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unipue: true|

### Association
- has_many :users, through: :group_users
- has_many :group_users
- has_many :articles


## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## articlesテーブル

|Column|Type|Options|
|------|----|-------|
|title|text|null: false,index: true|
|text|text|null: false,index: true|
|image|string|null: true|
|like|integer|
|user_id|integer|foreign_key: true|


### Association
- belongs_to :user
- has_many :comments
- has_many :likes

## likesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|article_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :article

## commentsテーブル

|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|string|null: true|
|user_id|integer|null: false, foreign_key: true|
|article_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :article
- belongs_to :user# editgate
