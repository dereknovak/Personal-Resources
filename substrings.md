### All possible substrings

```ruby
substrings = []

str.size.times do |start_idx|
  start_idx.upto(str.size - 1) do |end_idx|
    substrings << str[start_idx..end_idx]
  end
end
```