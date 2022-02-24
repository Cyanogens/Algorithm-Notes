递归形式--欧几里得算法(简洁)：
```java
public int gcd(int a, int b) {
	return b == 0 ? a : gcd(b, a % b);
}
```

迭代形式--更相减损法(精度高):
```java
public int gcd(int a, int b) {
	while (true){
		if (a > b){
			a -= b;
		}else if (a < b) {
			b -= a;
		}else {
			return a;
		}
	}
}
```