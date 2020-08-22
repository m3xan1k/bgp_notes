## Configuring iBGP connection between two routers in one AS that has address pool 17.0.0.0/8 and connection link to another AS 8.8.8.0/24


### Configure R1


1. Create BGP process 

```
router bgp <AS number>
```

2. Specify neighbor and same AS number

```
neighbor 17.0.1.2 remote-as <AS number>
```

3. Choose network to advertize

```
network 17.0.1.0 mask 255.255.255.0
```


### Configure R2

1. Start BGP process with same AS number as R1 does

```
router bgp <AS number>
```

2. Specify neighbor in same AS

```
neighbor 17.0.1.1 remote-as <AS number>
```

3. Advertize local and link networks

```
network 17.0.1.0 mask 255.255.255.0
network 8.8.8.0 mask 255.255.255.0
```

**iBGP in this AS established**

---

## Configure neighbor relationship between R2 and R3(another AS with prefix 15.0.0.0/8)


### Configure R2

1. Specify neighbor(R3) in a remote AS (bgp configuration mode)

```
neighbor 8.8.8.2 remote-as <AS number>
```

### Configure R3

1. Start BGP process with AS number that R3 belongs to

```
router bgp <AS number>
```

2. Specify neighbor(R2) and AS of R2

```
neighbor 8.8.8.1 remote-as <AS number>
```

3. Advertize networks

```
network 8.8.8.0 mask 255.255.255.0
network 15.0.1.0 mask 255.255.255.0
```

**Connectivity between two autonomous systems established**


---

## Finally configure iBGP in autonomous system with prefix 15.0.0.0/8


### Configure R3

1. Specify neighbor(R4) in same AS(bgp configuration mode)

```
neighbor 15.0.1.2 remote-as <AS number>
```

### Configure R4

1. Start BGP process

```
router bgp <AS number>
```

2. Specify neighbor(R3) in same AS

```
neighbor 15.0.1.1 remote-as <AS number>
```

3. Advertize network

```
network 15.0.1.0 mask 255.255.255.0
```

**iBGP in this AS established**

---

## Verifying commands

show BGP routing table

```
show ip bgp
```

verify neighbor status

```
show ip bgp summary
```

show neighbors in detail

```
show ip bgp neighbors
```

show established tcp sessions

```
show tcp brief
```
