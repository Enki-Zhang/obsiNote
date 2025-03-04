
## 基本语法

### <if> 标签
用于在条件成立时包含某部分 SQL。

```xml
<select id="findUserByName" resultType="User">
  SELECT * FROM users
  WHERE 1=1
  <if test="name != null">
    AND name = #{name}
  </if>
  <if test="age != null">
    AND age = #{age}
  </if>
</select>
```
- `test` 属性中的条件为 `true` 时，`<if>` 标签内的 SQL 会被加入。
- `#{name}` 用于占位符，MyBatis 会自动处理参数绑定。

###  `<choose>`、`<when>` 和 `<otherwise>` 标签

- `<choose>` 是条件选择的总容器，类似 `switch` 语句。
- `<when>` 标签为条件匹配，`<otherwise>` 提供默认值。

在 MyBatis 的 `<where>` 标签中，它会自动处理 SQL 语句的 `AND` 连接符。具体来说，`<where>` 标签的作用如下：

1. **如果内部有条件成立**（即 `if` 判断为 `true`），则 `where` 会自动添加 `WHERE` 关键字，并且会自动去掉第一个 `AND`，保证 SQL 语法正确。
2. **如果内部所有条件都不成立**（即 `if` 判断都为 `false`），那么 `where` 也不会出现，避免 `WHERE` 关键字单独存在导致的 SQL 语法错误。
## 常用sql查询