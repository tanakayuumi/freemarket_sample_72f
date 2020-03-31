# README
```
git clone https://github.com/ymkthr/freemarket_sample_72f.git
```

## DB設計
### Usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false|
|email|string|null: false, unique: true|
|password|string|null: false|
|age|integer|null: false|
|nickname|string|null: false, unique: true|
|address|string|null: false|
|value|integer||
|profile-text|text||
|profile-image|string||
#### Association
- has_many :items, through: :users_items
- has_many :users_items
- has_many :items, through: :likes
- has_many :likes
- has_many :items, through: :comments
- has_many :comments

### Users_Itemsテーブル
|Column|Type|Options|
|------|----|-------|
|buyer_id|integer||
|seller_id|integer|null:false|
|item_id|integer|null:false|
#### Association
belongs_to: user
belongs_to: item

### Itemsテーブル
|Column|Type|Options|
|------|----|-------|
|item-name|string|null: false|
|details|string|null: false|
|item_image_id|integer|null: false|
|sales_status|integer|null:false|
|item_status|integer|null: false|
|brand|string||
|category_id|integer|null: false|
|comment_id|integer||
|like_id|integer||
|price|integer|null: false|
|shipping_how_to|integer||
|shipping_area|integer|null: false|
|shipping_cost|integer|null: false|
|shipping_bays|string|null: false|
#### Association
- has_many :users, through: :users_items
- has_many :users_items
- has_many :item_images

### Item_imagesテーブル
|Column|Type|Options|
|------|----|-------|
|image_url|string|null: false|
|item_id|integer|null: false|
#### Association
- belongs_to :item


### Commentsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false|
|item_id|integer|null: false|
|text|text|null: false|
#### Association
belongs_to :user
belongs_to :item


### Likesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false|
|item_id|integer|null: false|
#### Association
- belongs_to :user
- belongs_to :item