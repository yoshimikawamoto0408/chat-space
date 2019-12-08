## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## users table
|Column|Type|Options|
|------|----|-------|
|name|string|null: index:true, null:false, unique:true|
|mail|string|null: false|

### Association
- has_many:groups,through:members
- has_many:messages
- has_many:members

## groups table
|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unipue: true|

### Association
- has_many :users, through: :group_users
- has_many :group_users
- has_many :messages

## message table
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|   |
|group|references|foreign_key: true|

### Association
- belongs_to :user
- belongs_to :groups