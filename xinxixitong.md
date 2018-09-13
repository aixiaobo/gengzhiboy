# gengzhiboy# First edition 第一版

information = dict()
list_1 = list()  # 定义空列表，准备存入相关信息

def pd():  # 添加函数
    # import datetime
    # time = datetime.datetime.now()
    name = input("姓名(name)：")
    password = input("密码(password)：")
    while True:
        if len(name) == 0:
            name = input("请输入正确的姓名(Please input the correct name)：")
        elif name in information:
            name = input("姓名已存在，请重新输入(Name already exists, Please re-enter):")
            password = input("密码(password)：")
        if len(password) == 0:
            password = input("密码不能为空，请重新输入（The password can not be empty， Please re-enter it）：")
        """接下来会获取异常：成绩score输入的是否为纯数字"""
        try:
            while True:
                score = int(input("成绩（score）："))
                if score > 100:
                    print("挺自信啊小兄弟,那你再输一遍吧")
                elif score < 0:
                    print("呵呵,莫不是在开玩笑,请再输一次")
                else:
                    break
        except Exception as q:
            print(q)   # 如出现异常，打印异常信息
            print("成绩必需是纯数字（Score must be pure numbers）")

        else:
            break
    information[name] = ({"name": name, "密码": password, "成绩": score})
    # print(information)

def rank():  # 排序函数
    for k, j in information.items():  # 将名字、成绩添加到list_1中
        list_1.append(j)
    list_1.sort(key=lambda a: a['成绩'], reverse=True)  # 对list_1按照'成绩'的键值进行降序排列
    # print(list_1)  # 打印排序结果


def query():  # 查询函数
    name = input('请输入需要查询的学生：')
    # 可以考虑使用for i in range进行优化
    for obj in list_1:
        if name in obj["name"]:
            print("成绩：", obj["成绩"], "名次：", int(list_1.index(obj) + 1))


print('__name__=', __name__)
if __name__ == "__main__":
    print("{:*^32}".format("学生信息录入及查询"))
    print("{:*^36}".format("命令列表"))
    print("{: ^36}".format("1:录入信息"))
    print("{: ^36}".format("2:停止录入"))
    print("{: ^36}".format("3:查询信息"))
    print("{: ^36}".format("4:退出系统"))
    print("{:*^40}".format("END"))
    while True:
        order = input("请输入您的命令：")
        if order == "1":
            pd()
            print(information)
        elif order == '2':
            rank()  # 结束输入后进行排名
        elif order == '3':
            query()
        elif order == '4':
            break

