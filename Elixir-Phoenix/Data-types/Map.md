# Maps %{}

## List all keys

```ex
Map.keys(my_query)
```
> [:__struct__, :assocs, :distinct, :from, :group_bys, :havings, :joins, :limit,
> :lock, :offset, :order_bys, :prefix, :preloads, :select, :sources, :updates,
> :wheres]

## Check if has a key

```ex
Map.has_key?(my_query, :from)
```
> true


## Access an element

```ex
my_query.from
```

## [Get first](https://joyofelixir.com/10-maps/)

```ex
Map.get("people") |> List.first
```

## [Traverse](https://hexdocs.pm/elixir/Enum.html)

```ex
iex> map = %{a: 1, b: 2}
iex> Enum.map(map, fn {k, v} -> {k, v * 2} end)
[a: 2, b: 4]
```

## Handle every element

* [Enum.reduce (robdor.com)](https://robdor.com/2015/01/22/elixir-enum-reduce/)

```ex
Enum.reduce [1, 2, 3], 100, fn(num, acc) ->
  num + acc
end
````
> 1 + 100

> 2 + 101

> 3 + 103

> = 106


## [Insert](https://hexdocs.pm/elixir/Map.html#put/3)

```x
data |> Map.put(:apple, data)
```

## [Group by](https://stackoverflow.com/a/40145358)

```ex
post_by_category = posts |> Enum.group_by(&(&1.category_id))
```

## Enum.each vs Enum.map

```ex
parsed = Enum.each(posts, fn post ->    
    post
end
```
> Will return :ok


```ex
parsed = Enum.map(posts, fn post ->
    post
end
```
> Will return [%{...},%{...}] 
Map returns a list that is the result

of applying that function to each element of the collection.