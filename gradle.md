

```
implementation: 字面意思是实现，实现就是我都已经实现了我的依赖，我的依赖上层就不用看了。
api: 字面意思是api,接口就会向上提供，我的依赖上层还是会看到，代替之前的compile
compile only: 和provided效果是一样的，只在编译的时候有效， 不参与打包
runtime only
test implementation
debug implementation
release implementation
```

 

api 需要使用

```groovy
plugins {
    id 'java-library'
}
```

