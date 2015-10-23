# the-rails-4-ways

Here is what I have learn from Ebook The Rails 4 way , Credit and Appreciate to Author.

2.2.11 Segment Key Constraint

- _:contraint_ : posibly with Regex.

Ex:

```ruby
  get ':controller/action/:id' => :show, contraints: {:id => /\d+/
  
  get ':controller/action/:id' => :show, id: /\d+/ (shorthand)
```
