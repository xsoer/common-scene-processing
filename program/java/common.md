- map操作
```java
// map声明
Map<String,String> map = new HashMap<>();
// 有序的map
LinkedHashMap<String, String> fieldMap = new LinkedHashMap<>();

// map添加
 map.put("SomeKey", "SomeValue”);

// map遍历
 map.forEach( (k,v) -> System.out.println("Key: " + k + ": Value: " + v));

// 获取所有的key
List<String> keyList = new ArrayList<>(map.keySet());

// 获取所有的value
map.valueSet()
```


- 正则表达式匹配
```java
String mulitSql = this.sqlUtils.readSql(sqlPath);
//声明正则
Pattern p = Pattern.compile("\\n;=\\w*\\n”);
// 正则匹配
Matcher m = p.matcher(mulitSql);
Map<String, List<Integer>> table = new HashMap<>();
int point = 0;
// 匹配结果遍历
while (m.find()) {
    table.put(m.group(), asList(point, m.start()));
    point = m.end();
}
```

- 动态生成TupleTypeInfo
```java
Class[] types = IntStream.range(0, size).mapToObj(i -> {
    if (flinkFieldType.get(i) == Types.INT) {
        return Integer.class;
    } else if (flinkFieldType.get(i) == Types.STRING) {
        return String.class;
    } else if (flinkFieldType.get(i) == Types.BIG_DEC) {
        return BigDecimal.class;
    } else if (flinkFieldType.get(i) == Types.SQL_TIMESTAMP) {
        return Timestamp.class;
    } else {
        return String.class;
    }
}).toArray(Class[]::new);

TupleTypeInfo<Tuple> typeInfo = TupleTypeInfo.getBasicAndBasicValueTupleTypeInfo(types);
```

- 字符串
```java
// 比较字符串
String.equals(“aaa”)
String.equalsIgnoreCase(str)

//判断字符串开头或结尾
String.startsWith(“aaa”)
String.endsWith(“bbb”)

// 截取字符串
String.substring(int beginIndex)
String.substring(int beginIndex, int endIndex)

// 子字符串
String.subSequence(int beginIndex, int endIndex)

// 对象转字符串
Object.toString()

// 字符串转数字
Integer.parseInt(String)

// 字符串切割
String[] String.split(String regex)
String[] String.split(String regex, int limit)

// 字符串长度
String.length()

// 判断字符串为零值
StringUtils.isBlank(str)
StringUtils.isNotBlank(str)

// 字符串比较
String.compareTo()

// 字符串链接
String.concat(String str)

// These two have the same value
new String("test").equals("test") // --> true 

// ... but they are not the same object
new String("test") == "test" // --> false 

// ... neither are these
new String("test") == new String("test") // --> false 

// ... but these are because literals are interned by 
// the compiler and thus refer to the same object
"test" == "test" // --> true 

// ... string literals are concatenated by the compiler
// and the results are interned.
"test" == "te" + "st" // --> true

// ... but you should really just call Objects.equals()
Objects.equals("test", new String("test")) // --> true
Objects.equals(null, "test") // --> false
Objects.equals(null, null) // --> true
```


- list操作
```java
// 是有序操作
// 声明list
List<String> list = new ArrayList<>();

// list添加
list.add(field);

// 删除一个元素
list.remove(int index)
list.remove(Object o)

// list获取值
list.get(0)

// 元素个数
list.size()

// 是否为空
list.isEmpty()

// 是否包含某个元素
list.contains(Object o)

// 转为数组
list.toArray()

// 清空
list.clear()

list.containsAll()

list.addAll()

list.indexOf(Object o)
list.lastIndexOf(Object o)

arrayList.set(int index, E element)

// 子list
list.subList(int fromIndex, int toIndex)
```


- 反射
```java
// 声明一个类并获取其实例
Class<?> c = HandleFunc.class;
Object obj = new Object();
obj = c.newInstance();

// 获取c类获取其方法，后边使其方法的参数
Method keyMethod = c.getMethod(funcString, Object.class);
// 执行改方法
key = keyMethod.invoke(obj, “aaa");
```

- 数据库连接
```java
// 原始链接
Class.forName(driverName);
conn = DriverManager.getConnection(jdbcUrl + db + "?useSSL=false", dbUserName, dbPasswd);
// 执行查询
Statement stmt = conn.createStatement();
String sql = "show columns from " + table;
ResultSet rs = stmt.executeQuery(sql);

// 链接池链接
MysqlPool mysqlPool = new MysqlPool(this.connectionConfig.getJdbcUrl(), this.connectionConfig.getUsername(), this.connectionConfig.getPassword());
Connection conn = mysqlPool.getConnection();
String sql = "show columns from " + this.table;
PreparedStatement statement = conn.prepareStatement(sql);
ResultSet rs = statement.executeQuery();

// 遍历结果集
while (rs.next()) {
    String field = rs.getString("Field").toLowerCase();
    String type = rs.getString("Type").toLowerCase();
    fieldMap.put(field, type);
}
mysqlPool.close(conn,statement,rs);
```


- 对象
```java
// 对象不能为空
Objects.requireNonNull(obj)
- 数据库
try{  
   Class.forName("com.mysql.jdbc.Driver");  
   Connection con=DriverManager.getConnection(  
 "jdbc:mysql://localhost:1521/xe","system","oracle");  
   
 PreparedStatement ps=con.prepareStatement("select - from emp");  
 ResultSet rs=ps.executeQuery();  
 ResultSetMetaData rsmd=rs.getMetaData();  
   
 System.out.println("Total columns: "+rsmd.getColumnCount());  
 System.out.println("Column Name of 1st column: "+rsmd.getColumnName(1));  
 System.out.println("Column Type Name of 1st column: "+rsmd.getColumnTypeName(1));  
   
 con.close();  
 }catch(Exception e){ System.out.println(e);}  
} 
```



