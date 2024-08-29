# One API Schema

## API Usage

### Key

API的名字，用户可使用Key来检索他们想要使用的API并根据API查询。

```
Key: ApiName
```

#### Current Key

**selectInfoById**

**selectNameByEmailLike**

**CountUsersByEmailLikeNameLike**

**selectInfoByAgeEs**

**selectInfoByAgeEs2**

### Inputs

一个列表，传递当前Key API所需要的参数

```
Inputs: [ Input1, Input2, ...]
```

#### Input

一个Map（Json转换自动写成Map，但其中只有一个Map.Entry），包含：{Key, Value}。其中Key是要替代的参数名字，Value是所要的替代的值。

```
Key: Value
```















