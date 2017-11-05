# An approach :Cartesian product

Cartesian product is a mathematical operation that returns a set (or product set or simply product) from multiple sets. 


![cp](https://github.com/orionbearduo/Markdown_pic/blob/master/cp.jpg)


### Process like this:

1.Select all distinct data from table Score as new table s2.
<br>```(select distinct Score from Scores) as s2;```

2.Make cartesian product(table Scores X table s2).condition will be : the score value in table Scores is less than or equal to talble s2.
<br>```select * from Scores as s1 left join (select distinct Score from Scores) as s2 on s1.Score <= s2.Score;```

New table is like this:

|s1.Score |id |s2.Score|
| :-:| :-:  |:-:|
|3.5|	1	|3.5|
|3.5	|1|	3.65|
|3.5|	1	|3.85|
|3.5|	1	|4.0|
|3.65|	2	|3.65|
|3.65|	2	|3.85|
|3.65|	2	|4|
4	|3|	4|
<br>
<b>Finally
```
select s1.Score as Score, count(s2.Score) as Rank from Scores as s1 left join (select distinct Score from Scores) as s2 on s1.Score <= s2.Score group by s1.id order by s1.Score desc;
```
