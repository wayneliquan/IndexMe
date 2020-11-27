java 基础类型转字节数组

[toc]

# Long to Bytes

```
public static byte[] LongToBytes(long values) {
    byte[] buffer = new byte[8];
    for (int i = 0; i < 8; i++) {
        int offset = 64 - (i + 1) * 8;
        buffer[i] = (byte) ((values >> offset) & 0xff);
    }
    return buffer;
}
```



# Bytes to Hex

```
public static String bytesToHex(byte[] bytes) {  
   StringBuffer sb = new StringBuffer();  
   for(int i = 0; i < bytes.length; i++) {  
       String hex = Integer.toHexString(bytes[i] & 0xFF);  
       if(hex.length() < 2){  
           sb.append(0);  
        }  
        sb.append(hex);  
    }  
    return sb.toString();  
} 
```

