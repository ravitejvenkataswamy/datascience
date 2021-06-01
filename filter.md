`filter(func,map_iterator)`
1. filter takes func as first input
1. and [[map]]_iterator as second iterator

Filter can run to exhaustion when we apply list

m = map(double, range(3,7))
f = lambda y : y >= 10
t = filter(f, m)
next(t)
3 => 6
4 => 8
5 => 10
10
next(t)
6 => 12
12
list(t)
[]
Here the becomes empty after the iteration of map
list(filter(f, map(double, range(3,7)))) 
3 => 6
4 => 8
5 => 10
6 => 12
[10, 12]
