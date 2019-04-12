# SQL & Query Plan 

## Twitter-Q1

### SQL:

```sql
ab = mjSession.sql("SELECT * FROM a, b WHERE a.y = b.y")
cd = mjSession.sql("SELECT * FROM c, d WHERE c.s = d.s")
ab.join(cd, $"b.z" === $"c.z" && $"a.x" === $"d.x")
```

### QueryPlan: 

#### HyMJ-H:

![image-20190411223051552](figure/t-q1-h.png)

#### HyMJ-E:

![t-q2](figure/t-q1-e.png)

## Twitter-Q2

### SQL:

```sql
gh = mjSession.sql("SELECT * FROM g, h WHERE g.q = h.q")
abef = mjSession.sql("SELECT * FROM a, b, e, f WHERE a.y = b.y AND b.z = e.z AND e.x = a.x AND e.z = f.z")
abef.join(gh, $"f.p" === $"g.p" && $"a.y" === $"h.y")
```

### QueryPlan: 

#### HyMJ-H:

![image-20190411223844316](figure/t-q2-h.png)

#### HyMJ-E:

![image-20190411223955770](figure/t-q2-e.png)

## Twitter-Q3

### SQL:

```sql
abef = mjSession.sql("SELECT * FROM a, b, e, f WHERE a.y = b.y AND b.z = e.z AND e.x = a.x AND e.z = f.z")
gij = mjSession.sql("SELECT * FROM g, i, j WHERE g.q = i.q AND i.r = j.r AND j.p = g.p")
abef.join(gij, $"f.p" === $"g.p")
```

### QueryPlan: 

#### HyMJ-H:

![image-20190411224018128](figure/t-q3-h.png)

#### HyMJ-E:

![image-20190411224035414](figure/t-q3-e.png)

## PPI-Q1

### SQL:

```sql
mjSession.sql("SELECT * FROM R, S, T WHERE R.b = S.b AND S.c = T.c")
```

### QueryPlan: 

#### HyMJ-H:

![image-20190411224450165](figure/p-q1-h.png)

#### HyMJ-E:

![image-20190411224512144](figure/p-q1-e.png)

## PPI-Q2

### SQL:

```sql
mjSession.sql("SELECT * FROM R, S, P WHERE R.b = S.b AND S.c = P.c AND P.a = R.a")
```

### QueryPlan: 

#### HyMJ-H:

![image-20190411224155178](figure/p-q2-h.png)

#### HyMJ-E:

![image-20190411224309018](figure/p-q2-e.png)

## PPI-Q3

### SQL:

```sql
val rsp = mjSession.sql("SELECT * FROM R, S, P WHERE R.b = S.b AND S.c = P.c AND P.a = R.a")
val tq = mjSession.sql("SELECT * FROM Q, T WHERE Q.d = T.d")
rsp.join(tq, $"R.a" === $"Q.a" && $"S.c" === $"T.c")
```

### QueryPlan: 

#### HyMJ-H:

![image-20190411224309018](figure/p-q3-h.png)

#### HyMJ-E:

![image-20190411224354382](figure/p-q3-e.png)

## DBLP-Q1

### SQL:

```sql
mjSession.sql(SELECT * FROM PA_1, PA_2, PC WHERE PA_1.pid = PC.pid AND PA_2.pid = PC.pid AND PA_1.aid = PA_2.aid)
```


### QueryPlan: 

#### HyMJ-H:

![image-20190411224624259](figure/d-q1-h.png)

#### HyMJ-E:

![image-20190411224639927](figure/d-q1-e.png)

## DBLP-Q2

### SQL:
```sql
mjSession.sql(SELECT * FROM PT, PA, CA, AN WHERE PT.pid = PA.pid AND PA.aid = CA.aid AND AN.aid = CA.coaid)
```


### QueryPlan: 

#### HyMJ-H:

![image-20190411224654697](figure/d-q2-h.png)

#### HyMJ-E:

![image-20190411224708090](figure/d-q2-e.png)

## DBLP-Q3

### SQL:

```sql
mjSession.sql(SELECT * FROM PA_1, PA_2, PC, CA, AN WHERE PA_1.pid = PC.pid AND PA_2.pid = PC.pid AND PA_1.aid = PA_2.aid AND PA_1.aid = CA.aid AND CA.coaid = AN.aid)
```

### QueryPlan:

#### HyMJ-H:

![image-20190411224741564](figure/d-q3-e.png)

#### HyMJ-E: 

![image-20190411224758813](figure/dblp-q3-e.png)