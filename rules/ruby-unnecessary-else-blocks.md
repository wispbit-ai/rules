---
include: "*.rb"
title: Avoid unnecessary else blocks in Ruby
tags: ruby,rails
---

Avoid unnecessary `else` blocks when the `if` block ends with a return statement, break, next, or similar control flow statements.

Bad:

```ruby
def process_value(value)
  if value > 10
    return "high"
  else
    return "low"
  end
end
```

```ruby
def check_items(items)
  items.each do |item|
    if item.length > 5
      puts "Long item: #{item}"
      next
    else
      puts "Short item: #{item}"
    end
  end
end
```

Good:

```ruby
def process_value(value)
  if value > 10
    return "high"
  end
  "low"
end
```

```ruby
def check_items(items)
  items.each do |item|
    if item.length > 5
      puts "Long item: #{item}"
      next
    end
    puts "Short item: #{item}"
  end
end
```
