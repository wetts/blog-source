```
<select id="getTotalBabyAttendCountByKid" resultType="map">
    SELECT sum(babysum) babyTotal, sum(brecordsum) babyAttendTotal
    FROM attend_babyrecord
    WHERE kindergarten_id = #{kid,jdbcType=INTEGER}
    AND class_id > 0
    AND attend_date = #{attendDate,jdbcType=VARCHAR}
</select>
```

如果返回值用 Map<String, Integer> ，会报异常：java.math.BigDecimal cannot be cast to java.lang.Integer

原因就是 sum() 的返回值类型为 java.math.BigDecimal 。

解决办法：
- 用 Map<String, Object> 接收返回值
通过 Integer.parseInt(obj.toString()) 得到需要的值

- 用 Map<String, BigDecimal> 接收返回值
通过 BigDecimal.intValue() 得到需要的值
