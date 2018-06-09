在开房数据中取出一条:

1、删除最后的换行符

2、获取该数据下的人名以及邮箱

3、将邮箱进行简单加密

4、拼接人名 + 性别 + 地址 + 加密邮箱,以’-’分隔。进阶：如何优化内存读取所有文本（Python生成式）



　　　　　file_path = 'C:\\Users\\hasee\\Desktop\\kaifangX.txt'

　　　　　open_file = open(file_path,'r',encoding='gbk')

输出法一：open_file.readline()
Out[3]: '陈萌,010-116321,M,19000101,北京市海淀区苏州街3号大恒科技大厦北座6层,100080,10116,010-82808028,010-82828028-208,chenmeng@dist.com.cn,0\n'

 输出法二：line = open_file.readline()

　　　　　line

Out[6]: '贾新格,0282,M,19000101,河北省石家庄栾城县城南一公里,051430,13831193762,0311-88030066,0311-88030088,info@shineway.com,0\n'

　　　　strip_line = line.strip('\n')

　　　　strip_line
Out[8]: '贾新格,0282,M,19000101,河北省石家庄栾城县城南一公里,051430,13831193762,0311-88030066,0311-88030088,info@shineway.com,0'

　　　　split_line = strip_line.split(',')

　　　　split_line
Out[10]: 
['贾新格',
 '0282',
 'M',
 '19000101',
 '河北省石家庄栾城县城南一公里',
 '051430',
 '13831193762',
 '0311-88030066',
 '0311-88030088',
 'info@shineway.com',
 '0']

 　　name = split_line[0]

　　name
Out[12]: '贾新格'

　　email = split_line[-2]

　　email
Out[14]: 'info@shineway.com'

　　　new_email = ''

　　　for i in email:
    　　new_email = ''.join((new_email,chr(ord(i) +1)))
   　　 print(new_email)
    　　new_email
    
j
jo
jog
jogp
jogpA
jogpAt
jogpAti
jogpAtij
jogpAtijo
jogpAtijof
jogpAtijofx
jogpAtijofxb
jogpAtijofxbz
jogpAtijofxbz/
jogpAtijofxbz/d
jogpAtijofxbz/dp
jogpAtijofxbz/dpn

　　　　　　　 name
Out[17]: '贾新格'

连接法一　　name +'-' +new_email
Out[18]: '贾新格-jogpAtijofxbz/dpn'

连接法二　　'-'.join((name,new_email,split_line[3],split_line[-1]))
Out[19]: '贾新格-jogpAtijofxbz/dpn-19000101-0'