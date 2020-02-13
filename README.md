![Untitled Diagram](https://user-images.githubusercontent.com/57151814/74227619-330d3b80-4d02-11ea-8077-e8d5744f8922.jpg)

# DB設計
 
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false|
|first_name|string|null: false|
|last_name|string|null: false|
|first_furigana|string|
|last_furigana|string|
|birth_year|integer|null: false|
|birth_month|integer|null: false|
|birth_day|integer|null: false|
|post_number|integer|null: false|
|prefecture|string|null: false|

|municipality|string|null: false|
|house_number|string|null: false|
|tel|integer|unique|
|icon|stirng|
 
### Association
- has_many :comments
- has_many :evaluations
- has_many :credit_cards
- has_many :likes, dependent: :destroy
- has_many :itmes_users
- has_many :items, through: :items_users
- has_many :liked_items, through: :likes, source: :items
 
## commentテーブル
|Column|Type|Options|index|
|------|----|-------|-----|
|comment|text|
|user_id|references|null: false, foreign_key: true|○|
|item_id|references|null: false, foreign_key: true|○|
 
### Association
- belongs_to :user
- belongs_to :item
 
## items_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|item_id|references|null: false, foreign_key: true|
 
### Association
- belongs_to :item
- belongs_to :user
 
## likesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|item_id|references|foreign_key: true|
 
### Association
- belongs_to :item
- belongs_to :user
 
## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|price|integer|null: false|


|condition|string|null: false|
|size|string|null: false|
|shippsing_charges|stirng|null: false|
|shipping_method|string|null: false|
|shipping_area|string|null: false|
|estimated_shipping_fee|string|null: false|
|introduction|text|null: false|
|sales_status|string|null: false|

###  Association
- belongs_to :user
- belongs_to :bland
- has_many :comments
- has_many :item_categories
- has_many :categories, through: :item_categories
- has_many :likes, dependent: :destroy
- has_many :liked_users, through: :likes, source: :user

## shippsingテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|item_id|references|foreign_key: true|
|burden|string|null: false|
|method|string|null: false|
|area||string|null: false|
|estimated|string|null: false|

###  Association
- belongs_to :user
- belongs_to :item


## item_categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|item_id|references|null: false, foreign_key: true|
|category_id|references|null: false, foreign_key: true|
 
### Association
- belongs_to :item
- belongs_to :category
 
## categoriesテーブル
 
### Association
- has_many :ancestry
 
 
## evaluationテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|item_id|references|null: false, foreign_key: true|
|comment|text|
 
### Association
- belongs_to :user
- belongs_to :item
 
 
## credit_cardテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|Card_information|integer|
 
### Association
- belongs_to :user
