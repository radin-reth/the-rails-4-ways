# the-rails-4-ways

Here is what I have learn from Ebook The Rails 4 way , Credit and Appreciate to Author.

2.2.11 Segment Key Constraint

- _:contraint_ : posibly with Regex.

Ex:

```ruby
  get ':controller/action/:id' => :show, contraints: {:id => /\d+/  
  get ':controller/action/:id' => :show, id: /\d+/ (shorthand)
```

it also check for request attribute that return a string.

```ruby
  get ':controller/action/:id' => :show, containts: { subdomain: 'admin' } # request.subdomain
```

- Full access to request object.

# protect records with id under 100
get 'records/:id' => 'records#protected',
    contraints: proc { |req| req.params[:id].to_i < 100 }

2.2.12 The Root Route

```ruby
  root to: 'welcome#index'
  root 'welcome#index' (shorthand)
```

2.3 Route Globbing

url:
/items/list/base/books/fiction/dickens

route:
get 'items/list/*specs', controller: 'items', action: 'list'

params:
params[:specs] # e.g, "base/books/fiction/dickens"

+ Globbing Key-Value Pairs
http://localhost:3000/items/q/field1/value1/field2/value2/...

```ruby
  get 'items/q/*specs', controller: "items", action: "query"
```
Then
```ruby
  @items = Item.where(Hash[*params[:specs].split("/")])
```

### In-depth knowledge of Ruby is a prerequisite for becoming an expert Rails developer ###

2.4 Named Routes

- name_url:
- name_path: no protocol, no host

2.4.1 Creating a Named Route

- using optional _:as_ parameter

```ruby
  get 'help' => 'help#index', as: 'help'
```

=> link_to "Help", help_path # /help

2.4.2 name_path vs. name_url

- redirect should use name_url
- name_path occur in view template(link_to, form_for)

+ Literals URL

link_to "Help", controller: "main", action: "help"
link_to "Help", "/main/help"



