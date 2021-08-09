Resource
- Users - create users table and model
        - add validations
        * username must be present and unique, min 3 max 25
        * email address must be present and unique, max 105
        * email must be valid email format, check with email regex

Associations
- One-to-many
  between users and articles

REST for users

Authentication
- Login using secure password

Restriction of actions
- Based on logged in/logged out state

Security
- Admin user functionality and access level




You're running bundle exec on a program. The program's creators wrote it when certain versions of gems were available. The program Gemfile specifies the versions of the gems the creators decided to use. That is, the script was made to run correctly against these gem versions.

Your system-wide Gemfile may differ from this Gemfile. You may have newer or older gems with which this script doesn't play nice. This difference in versions can give you weird errors.

bundle exec helps you avoid these errors. It executes the script using the gems specified in the script's Gemfile rather than the systemwide Gemfile. It executes the certain gem versions with the magic of shell aliases.

Here's an example Gemfile:
```
source 'http://rubygems.org'

gem 'rails', '2.8.3'
```
Here, bundle exec would execute the script using rails version 2.8.3 and not some other version you may have installed system-wide.

` bundle exec rake db:migrate `

` bundle exec rails c`

```
rails generate migration create_articles
rails db:migrate
rails db:rollback
rails generate migration add_timestamps_to_articles
rails db:migrate
```


```
 rails c
 > article = Article.new(title:"thrid article", description: "description")
 > article.save
 > Article.all
```


```
irb(main):003:0> Article.find(1)
  Article Load (0.7ms)  SELECT "articles".* FROM "articles" WHERE "articles"."id" = ? LIMIT ?  [["id", 1], ["LIMIT", 1]]
=> #<Article id: 1, title: "first article", description: "description", created_at: "2021-08-06 02:24:20.329179000 +0000", updated_at: "2021-08-06 02:24:20.329179000 +0000">

irb(main):004:0> Article.find(2)
  Article Load (0.3ms)  SELECT "articles".* FROM "articles" WHERE "articles"."id" = ? LIMIT ?  [["id", 2], ["LIMIT", 1]]
=> #<Article id: 2, title: "second article", description: "description of second", created_at: "2021-08-06 02:25:56.096044000 +0000", updated_at: "2021-08-06 02:25:56.096044000 +0000">

irb(main):005:0> Article.first
  Article Load (0.4ms)  SELECT "articles".* FROM "articles" ORDER BY "articles"."id" ASC LIMIT ?  [["LIMIT", 1]]
=> #<Article id: 1, title: "first article", description: "description", created_at: "2021-08-06 02:24:20.329179000 +0000", updated_at: "2021-08-06 02:24:20.329179000 +0000">

irb(main):006:0> Article.last
  Article Load (0.4ms)  SELECT "articles".* FROM "articles" ORDER BY "articles"."id" DESC LIMIT ?  [["LIMIT", 1]]
=> #<Article id: 2, title: "second article", description: "description of second", created_at: "2021-08-06 02:25:56.096044000 +0000", updated_at: "2021-08-06 02:25:56.096044000 +0000">
irb(main):007:0> 


article = Article.find(2)

article.description
article.description = "asdf"
article.save

article = Article.last
article.destroy
```


```
irb(main):015:0> article = Article.new
   (0.3ms)  SELECT sqlite_version(*)
   
irb(main):016:0> article.save
=> false

irb(main):017:0> article.errors
=> #<ActiveModel::Errors:0x0000561eefa0fe88 @base=#<Article id: nil, title: nil, description: nil, created_at: nil, updated_at: nil>, @errors=[#<ActiveModel::Error attribute=title, type=blank, options={}>]>

irb(main):018:0> article.errors.full_messages
=> ["Title can't be blank"]

```

```
rails routes --expanded
```

```
rails generate scaffold User username:string
```
This command will create a db/migrate/20200402140641_create_users.rb file
```
rails db:migrate
```
Then go to console

```
User.all

User

User.create(username: "mashrur")

User.create(username: "john")
```

Lets add relation

```
rails generate migration add_user_id_to_articles

# add_user_id_to_articles.rb
class AddUserIdToArticles < ActiveRecord::Migration[6.0]
    def change
        add_column :articles, :user_id, :int
    end
end

rails db:migrate

Article.all

Article.create(title: "some article", description: "description of some article", user_id: user_1.id)
Article.create(title: "some article", description: "description of some article", user_id: user_1)

user_1 

user_1.articles


user_1.articles.build(title:"some new article", description:"description of some new articles")
// this will add an article to the user

article = _ 
// the return from previous cmd

article.save

article.last

user_1.articles




user_2.articles
article = Article.first
user_2.articles << article
```


Without scafolder
```
rails generate migration create_users
```







