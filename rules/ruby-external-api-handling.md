---
include: "app/controllers/**/*.rb"
title: External API error handling in Ruby
tags: ruby,rails
---

When making external API requests, implement proper error handling with descriptive logging to help with debugging issues.

Bad:

```ruby
def fetch_external_data
  response = HTTParty.get("https://api.example.com/data")
  JSON.parse(response.body)
end
```

Good:

```ruby
def fetch_external_data
  response = HTTParty.get("https://api.example.com/data")

  if response.success?
    JSON.parse(response.body)
  else
    Rails.logger.error("API request failed: status=#{response.code}, message=#{response.message}, body=#{response.body}")
    nil
  end
end
```
