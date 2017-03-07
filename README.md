# pyinstaller-
解决pyinstaller不支持中文路径的问题，方法如下：

修改 C:\Python27\Lib\site-packages\pkg_resources\__init__.py ：1522行中的 _fn函数定义如下：
def _fn(self, base, resource_name):

        if resource_name:
        
            try:
            
                  return os.path.join(base, *resource_name.split('/'))
                  
            except:
            
                  return os.path.join(base, *resource_name.decode('gb18030').encode('utf-8').split('/'))
                  
        return base

注：本人在 pyinstaller v3.3 32bit环境测试有效
