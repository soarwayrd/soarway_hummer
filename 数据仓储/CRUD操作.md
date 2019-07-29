框架在`BaseRepository`类里实现了一套封装了简单CRUD操作。下面以`UserRepository`为例演示CRUD的基础使用。

1. Create - 新增
   
   ```csharp
   // 新增单条数据
   _userRepository.Create(new User() { UserName = "张三", Password = "abc123", Gender = true, IsLock = false });

   // 批量新增多条数据
   _userRepository.Creates(new List<User>() {
        new User() { UserName = "李四", Password = "abc123", Gender = true, IsLock = false } ,
        new User() { UserName = "王五", Password = "abc123", Gender = false, IsLock = false }});
   ```

2. Delete - 删除
   
   ```csharp
   // 根据实体删除单条数据
   var user = _userRepository.GetByPrimaryKey(1);
   _userRepository.Delete(user);

   // 根据主键删除单条数据
   _userRepository.Delete(1);

   // 根据主键集合，批量删除数据
   _userRepository.Deletes(new List<object>() { 1, 2, 3, 4, 5 });

   // 根据实体集合，批量删除数据
   var users = _userRepository.FindBySpecification(x => x.UserID > 0);
   _userRepository.Deletes(users);
   ```

3. Update - 修改
   
   ```csharp
   // 修改一个实体
   var user = _userRepository.GetByPrimaryKey(1);
   user.UserName = "赵六";
   user.IsLock = false;
   _userRepository.Update(user);
   
   // 根据ID，修改单条数据的部分字段
   _userRepository.Update(1, new ModifyDefine<User>(x => x.UserName, "赵六"), new ModifyDefine<User>(x => x.IsLock, false));
 
   // 根据ID，修改单条数据的部分字段
   _userRepository.Update(1, new ModifyDefine("UserName", "赵六"), new ModifyDefine("IsLock", false));

   // 根据实体集合，批量更新数据
   var users = _userRepository.FindBySpecification(x => x.UserID > 0).ToList();
   users.ForEach(x => x.Enable = false);
   _userRepository.Updates(users);

   ```

4. Select - 查询
   
   >查询功能分为查询单个实体和查询IQueryable对象，
   除了函数名不一样外，查询单个实体和查询IQueryable对象拥有一样的参数列表，
   及对称的方法重载数量
   查询单个实体的函数均为 T GetBySpecification 开头
   查询IQueryable对象的函数均为 IEnumerable<T> FindBySpecification 开头

  ```csharp

   // 根据ID获取单个实体
   _userRepository.GetByPrimaryKey(1);
   ```