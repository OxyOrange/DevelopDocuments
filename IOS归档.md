# IOS归档

    归档是IOS中常用的一种数据存贮方式，几乎任何类型的对象都能够被归档储存（实际上是一种文件保存的形式）。
    与属性列表相反，同样作为轻量级存储的持久化方案，数据归档是进行加密处理的，数据在经过归档处理会转换成二进制数据，所以安全性要远远高于属性列表。
    我们可以将复杂的对象写入文件中，并且不管添加多少对象，将对象写入磁盘的方式都是一样的。

#### 使用 NSKeyedArichiver 

    1、归档单个对象
        NSArray *array = [NSArray arrayWithObjects:@1,@2,@3, nil];
        NSString *filePath = [NSHomeDirectory() stringByAppendingString:@"testFile.plist"];    
        BOOL success = [NSKeyedArchiver archiveRootObject:array toFile:filePath];
    2、归档多个对象
        NSMutableArray *array = [NSMutableArray arrayWithObjects:@"BigDragon",@"BigBiao",@"BigBaby", nil];
        NSMutableData *data = [NSMutableData data];
        NSKeyedArchiver *archiver = [[NSKeyedArchiver alloc] initForWritingWithMutableData:data];

        [archiver encodeObject:array forKey:@"array"];
        [archiver encodeObject:@"Jason‘s friends" forKey:@"name"];
        
        //编码完成之后，对象已经存储到data之中。
        [archiver finishEncoding];
        
        NSString *filePath = [NSHomeDirectory() stringByAppendingPathComponent:@"array.plist"];
        BOOL success = [data writeToFile:filePath atomically:YES];

#### 使用 NSKeyedUnarchiver 解档

    1、解档单个对象
        NSString *filePath = [NSHomeDirectory() stringByAppendingString:@"testFile.plist"];
        id array = [NSKeyedUnarchiver unarchiveObjectWithFile:filepath];
    2、解档多个对象
        NSString *filePath = [NSHomeDirectory() stringByAppendingPathComponent:@"array.plist"];
        NSData *data = [[NSData alloc] initWithContentsOfFile:filePath];
        NSKeyedUnarchiver *unarchiver = [[NSKeyedUnarchiver alloc] initForReadingWithData:data];
        NSArray *array = [unarchiver decodeObjectForKey:@"array"];
        NSString *name = [unarchiver decodeObjectForKey:@"name"];


## 归档自定义对象

    注意：自定义对象的归档需要遵循 NSCoding 协议
![](https://github.com/zhanghouqi/DevelopDocuments/blob/master/Images/归档图.png)
