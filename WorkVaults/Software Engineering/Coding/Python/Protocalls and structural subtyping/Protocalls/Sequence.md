- Requires that: 
	- Items can be retrieved using square brackets with an integer index
	- That items can be searched for with index
	- That items can be counted with count, and that a 
	- Reversed copy of the sequence can be produced
- Objects that support sequence must also support [[Iterable]], [[Sized]], and [[Container]]
```Python
item = sequence[index]
i = sequence.index(item)
num = sequence.count(item
r = reversd(sequence))
```