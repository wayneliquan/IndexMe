Java 有符号和无符号类型的相互转化

[toc]

# Unsigned long to java Long

To BigInteger

```
private static BigInteger toUnsignedBigInteger(long i) {
    if (i >= 0L)
        return BigInteger.valueOf(i);
    else {
        int upper = (int) (i >>> 32);
        int lower = (int) i;
        // return (upper << 32) + lower
        return (BigInteger.valueOf(Integer.toUnsignedLong(upper)))
        				  .shiftLeft(32)
        				  .add(BigInteger.valueOf(Integer.toUnsignedLong(lower)));
        }
    }

```

To BigDecimal

```
public static final BigDecimal readUnsignedLong(long value) {
    if (value >= 0)
        return new BigDecimal(value);
    long lowValue = value & 0x7fffffffffffffffL;
    return BigDecimal.valueOf(lowValue).add(BigDecimal.valueOf(Long.MAX_VALUE)).add(BigDecimal.valueOf(1));
}
```



