# 笔试题  
# 填写人: 冯梦健  应聘职位: python后端

请完成以下笔试题，可以使用自己擅长的语言来编写，通过 github pull request 提交代码。

1. 编写一个递归版本的 reverse(s) 函数(或方法),以将字符串s倒置。
def func(str):
    if str:
        return func(str[1:]) + str[0]
    else:
        return str

2. 编写程序 expr，以计算从命令行输入的逆波兰表达式的值，其中每个运算符或操作数用一个单独的参数表示。例如，命令
expr 2 3 4 + *

str1 = 'expr 2 3 4 + *'
nums = []
for c in str1.split():
    if c in '+-*':
        i2 = nums.pop()
        i1 = nums.pop()
        nums.append(str(eval(i2 + c + i1)))
    else:
        nums.append(c)

    return eval(nums.pop()) 





3. 用归并排序将3，1，4，1，5，9，2，6 排序。
seq = 3，1，4，1，5，9，2，6

def merge_sort(seq):
    if len(seq) <= 1:   # 递归出口
        return seq
    else:
        mid = int(len(seq)/2)
        left_half = merge_sort(seq[:mid])
        right_half = merge_sort(seq[mid:])

        # 合并两个有序
        new_seq = merge_sorted_list(left_half, right_half)
        return new_seq

def merge_sorted_list(sorted_a, sorted_b):
    """ 合并两个有序序列，返回一个新的有序序列
    """
    length_a, length_b = len(sorted_a), len(sorted_b)
    a = b = 0
    new_sorted_seq = list()

    while a < length_a and b < length_b:
        if sorted_a[a] < sorted_b[b]:
            new_sorted_seq.append(sorted_a[a])
            a += 1
        else:
            new_sorted_seq.append(sorted_b[b])
            b += 1
    if a < length_a:
        new_sorted_seq.extend(sorted_a[a:])
    else:
        new_sorted_seq.extend(sorted_b[b:])

    return new_sorted_seq


4. 对下面的 json 字符串 serial 相同的进行去重。

```javascript
  [{
    "name": "张三",
    "serial": "0001"
  }, {
    "name": "李四",
    "serial": "0002"
  }, {
    "name": "王五",
    "serial": "0003"
  }, {
    "name": "王五2",
    "serial": "0003"
  }, {
    "name": "赵四",
    "serial": "0004"
  }, {
    "name": "小明",
    "serial": "005"
  }, {
    "name": "小张",
    "serial": "006"
  }, {
    "name": "小李",
    "serial": "006"
  }, {
    "name": "小李2",
    "serial": "006"
  }, {
    "name": "赵四2",
    "serial": "0004"
  }];
```

item = [{
    "name": "张三",
    "serial": "0001"
  }, {
    "name": "李四",
    "serial": "0002"
  }, {
    "name": "王五",
    "serial": "0003"
  }, {
    "name": "王五2",
    "serial": "0003"
  }, {
    "name": "赵四",
    "serial": "0004"
  }, {
    "name": "小明",
    "serial": "005"
  }, {
    "name": "小张",
    "serial": "006"
  }, {
    "name": "小李",
    "serial": "006"
  }, {
    "name": "小李2",
    "serial": "006"
  }, {
    "name": "赵四2",
    "serial": "0004"
  }];


  d_list = []
  dict_list2 = []
  for dict_item in d:
     val_a = dict_item['name']
     val_b = dict_item['serial']
     new_tuple = (val_a,val_b,)
     if new_tuple not in d_list:
          d_list.append(new_tuple)
          dict_list2.append(dict_item)
     else:
          print('被移除的元素', dict_item)
  print(dict_list2) 


5. 把下面给出的扁平化json数据用递归的方式改写成组织树的形式

```javascript
  [
    {
      "id": "1",
      "name": "中国",
      "code": "110",
      "parent": ""
    },
    {
      "id": "2",
      "name": "北京市",
      "code": "110000",
      "parent": "110"
    },
    {
      "id": "3",
      "name": "河北省",
      "code": "130000",
      "parent": "110"
    },
    {
      "id": "4",
      "name": "四川省",
      "code": "510000",
      "parent": "110"
    },
    {
      "id": "5",
      "name": "石家庄市",
      "code": "130001",
      "parent": "130000"
    },
    {
      "id": "6",
      "name": "唐山市",
      "code": "130002",
      "parent": "130000"
    },
    {
      "id": "7",
      "name": "邢台市",
      "code": "130003",
      "parent": "130000"
    },
    {
      "id": "8",
      "name": "成都市",
      "code": "510001",
      "parent": "510000"
    },
    {
      "id": "9",
      "name": "简阳市",
      "code": "510002",
      "parent": "510000"
    },
    {
      "id": "10",
      "name": "武侯区",
      "code": "51000101",
      "parent": "510001"
    },
    {
      "id": "11",
      "name": "金牛区",
      "code": "51000102",
      "parent": "510001"
    }
  ];
```



dict1=[
    {
      "id": "1",
      "name": "中国",
      "code": "110",
      "parent": ""
    },
    {
      "id": "2",
      "name": "北京市",
      "code": "110000",
      "parent": "110"
    },
    {
      "id": "3",
      "name": "河北省",
      "code": "130000",
      "parent": "110"
    },
    {
      "id": "4",
      "name": "四川省",
      "code": "510000",
      "parent": "110"
    },
    {
      "id": "5",
      "name": "石家庄市",
      "code": "130001",
      "parent": "130000"
    },
    {
      "id": "6",
      "name": "唐山市",
      "code": "130002",
      "parent": "130000"
    },
    {
      "id": "7",
      "name": "邢台市",
      "code": "130003",
      "parent": "130000"
    },
    {
      "id": "8",
      "name": "成都市",
      "code": "510001",
      "parent": "510000"
    },
    {
      "id": "9",
      "name": "简阳市",
      "code": "510002",
      "parent": "510000"
    },
    {
      "id": "10",
      "name": "武侯区",
      "code": "51000101",
      "parent": "510001"
    },
    {
      "id": "11",
      "name": "金牛区",
      "code": "51000102",
      "parent": "510001"
    }
  ]


def func(i, items):
    for index, item in enumerate(items):
        if i['parent'] == item['code']:
            i['parent'] = item
            if item['parent']:
                func(item, items)

for i in items:
    func(i, items)
