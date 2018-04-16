# User Songs

This rails app is a one model app that has a single `Song` model. A song has a title.

Your job is to implement best security practices for this app:

User login and authorization with devise.

We will follow instuctions from the devise website:
[https://github.com/plataformatec/devise](https://github.com/plataformatec/devise)

Add the gem devise to the Gemfile
```
gem 'devise'
```
Install it
```
bundle install
```
Run the gem's script files so it can generate the default files in the rails app
```
rails generate devise:install
```

Create the devise user model:
```
rails generate devise user
```

Generate the default devise view files:
```
rails g devise:views
```

```
rails db:migrate
```

Devise might ask you to copy the secret devise key into the initializer file: config/initializers/devise.rb

Add a before action filter to the controller:
```
before_action :authenticate_user!, :except => [ :show, :index ]
```

Restrict the new link in the songs index with the devise helper
```
<% if user_signed_in? %>
<%= link_to 'New Song', new_song_path %>
<% end %>
```
