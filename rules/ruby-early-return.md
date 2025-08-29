---
include: "*.rb"
title: Early returns in Ruby
tags: ruby,rails
---

Use early returns to reduce nesting levels. Prefer checking error conditions or guard clauses first and returning early, rather than wrapping the main logic in deep conditional blocks.

Bad

```ruby
def process_data(data)
  if data.present?
    if valid?(data)
      result = ""
      data.each do |item|
        if item.present?
          # More nested code here
          result += transform(item)
        end
      end
      { success: result }
    else
      { error: "invalid data" }
    end
  else
    { error: "empty data" }
  end
end
```

Good

```ruby
def process_data(data)
  return { error: "empty data" } if data.empty?
  return { error: "invalid data" } unless valid?(data)

  result = ""
  data.each do |item|
    next if item.blank?
    result += transform(item)
  end

  { success: result }
end
```
