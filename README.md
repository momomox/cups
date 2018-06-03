#DB設計

## membersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|index: true, null: false, unique: true|
|email|string|null: false, unique: true|
|image|string||

### Association
- has_many :messages
- has_many :comments
- belongs_to :listner

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|text|string|null: false|
|member_id|integer|null: false, foreign_key: true|
|lisner_id|integer|foreign_key: true|
|group_id|integer|foreign_key: true|

### Association
- belongs_to :member
- belongs_to :listner
- belongs_to :group

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :messages

## forumテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|member_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :member
- has_many :comments

## commentsテーブル

|Column|Type|Options|
|------|----|-------|
|text|string|null: false|
|member_id|integer|null: false, foreign_key: true|
|forum_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :member
- belongs_to :forum

