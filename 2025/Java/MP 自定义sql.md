
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