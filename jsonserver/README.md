// 获取所有的用户信息
http://localhost:3000/user

// 获取id 为1 的用户信息
http://localhost:3000/user/1

// 获取company 的所有信息
http://localhost:3000/companies

获取所有公司id 为 3 的 用户
http://localhost:3000/companies/3/user

根据公司名字获取信息
http://localhost:3000/companies?name=Orange

根据公司多个名字获取信息
http://localhost:3000/companies?name=Orange&name=Apple

获取一页中只有两条数据（分页）
http://localhost:3000/user?_page=1&_limit=2

根据name升序排序（ asc 升序  desc 降序）
http://localhost:3000/user?_sort=name&_order=asc

获取年龄为28 及 28以上的
http://localhost:3000/user?age_gte=28

获取年龄区间 为 28 -  38 的
http://localhost:3000/user?age_gte=28&age_lte=38

根据搜索信息
http://localhost:3000/user?q=zhang