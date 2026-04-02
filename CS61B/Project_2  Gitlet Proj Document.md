
## Lab06 Gitlet前置
python global environment - **homebrew**
python work environment - **miniconda**
#### Java项目管理内容：

	javac -- 编译运行
	java -- 运行
	make -- 编译
	make check -- 编译并运行Check
	cd .. -- 父级文件夹
	cd ../..

#### Java文件读写

```java
//创建文件--注意 此时在Finder里还找不到这个文件，没有被生成
File f = new File("dummy.txt");
//真正能在Finder里找到
f.createNewFile();
//验证存在性
f.exists()
//引入Utils库莱写入内容
Utils.writeContents(f, "Hello World");
//创建文件目录
File d = new File("dummy");
//创建文件夹--Finder能找到
d.mkdir();
```

#### Serializable 序列化

序列化是将一个对象转换成一系列字节，然后存储在文件中的过程。之后，我们可以反序列化这些字节，并在程序下次运行时获取原始对象。

示例：引入这个接口Serializable
```java
import java.io.Serializable;

public class Model implements Serializable {
    ...
}
```

借助Utils库 - 序列化和反序列化
```java
Model m;
File outFile = new File(saveFileName);

// Serializing the Model object
writeObject(outFile, m);
```
```java
Model m;
File inFile = new File(saveFileName);

// Deserializing the Model object
m = readObject(inFile, Model.class);
```
