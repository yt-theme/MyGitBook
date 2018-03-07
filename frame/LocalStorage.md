 ### 数据长期存于本地
    // 对象转换成性json对象
    const info = {
            name: 'Lee',
            age: 20,
            id: '001'
        };
        sessionStorage.setItem('key', JSON.stringify(info));
        localStorage.setItem('key', JSON.stringify(info));

### 获取数据
    var data1 = JSON.parse(sessionStorage.getItem('key'));
    var data2 = JSON.parse(localStorage.getItem('key'));
    
### 删除某个保存的数据
    sessionStorage.removeItem('key');
    localStorage.removeItem('key');
    
### 删除所有数据
    sessionStorage.clear();
    localStorage.clear();
    
### 监听数据变化
     window.addEventListener('storage', function (e) {
        console.log('key', e.key);
        console.log('oldValue', e.oldValue);
        console.log('newValue', e.newValue);
        console.log('url', e.url);
    })
