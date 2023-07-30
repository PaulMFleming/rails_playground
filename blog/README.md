# Basic Blog App

* Built following [Ruby On Rails - getting started](https://guides.rubyonrails.org/getting_started.html) guide

## Things learned from this project
- Creating a new Rails project
```
rails new project_name
```
- Starting the rails local web server
```
bin/rails server
```
- Setting up index page & other routes
```
Rails.application.routes.draw do
  root "articles#index"

  get "/articles", to: "articles#index"
end
```
- Generating models
```
bin/rails generate model Article title:string body:text
```
- Database migrations
```
bin/rails db:migrate
```
- Using a model to interact with a database
```
bin/rails console
irb> article = Article.new(title: "Hello Rails", body: "I am on Rails!")
irb> article.save
irb> article
=> #<Article id: 1, title: "Hello Rails", body: "I am on Rails!", created_at: "2020-01-18 23:47:30", updated_at: "2020-01-18 23:47:30">
Article.find(1)
Article.all

```
- CRUD ops for blog articles
    * define methods in relevant controllers
- Adding additional models & Associating models
- Updating routes (using `resouces`)
```
Rails.application.routes.draw do
  root "articles#index"

  resources :articles
end

```
- Generating controllers
```
 bin/rails generate controller Comments
```
- Rendering partial collections & forms
    * D.R.Y.
- Using concerns
    * D.R.Y. (concerns are like mixins)
- Deleting associated objects (with `dependent`)
```
class Article < ApplicationRecord
  include Visible

  has_many :comments, dependent: :destroy

  validates :title, presence: true
  validates :body, presence: true, length: { minimum: 10 }
end
```

- Basic http auth
    * using the `http_basic_authenticate_with` Rails method 