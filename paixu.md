# gengzhiboydef showInFo():
    print("_"*30)
    print("学生管理系统 v1.0")
    print("1.添加学生的信息")
    print("2.删除学生的信息")
    print("3.修改学生的信息")
    print("4.查询学生的信息")
    print("5.查询学生的排名")
    print("6.退出系统")
    print('_'*30)
s=[]
while True:
    showInFo()
    key=int(input('请选择功能（序号）：'))
    if key==1:
        print("您选择了添加学生信息功能")
        name=input("请输入学生姓名：")
        stuId=input("请输入学生学号(学号不可重复)")
        age=input("请输入学生年龄:")
        object=input("请输入学科")
        score=input("请输入分数")
        i=0
        leap=0
        for temp in s:
            if temp['id']==stuId:
                leap=1
                break
            else:
                i=i+1
        if leap ==1:
            print("输入学生学号重复，添加失败！")
            continue
        else:
            temp = {}
            temp['name']=name
            temp['id']=stuId
            temp['age']=age
            temp['object']=object
            temp['score']=score
            s.append(temp)
            print('添加成功！')
    elif key==2:
        print("您选择了删除学生功能")
        delId=input('请输入要删除的学生号：')
        i=0
        leap=0
        for temp in s:
            if temp['id']==delId:
                leap=1
                break
            else:
                i=i+1
        if  leap==0:
            print('没有此学生学号，删除失败！')
        else:
            del s[i]
            print('删除成功！')
    elif key==3:
        print("您选择了修改学生信息功能")
        alterId=input('请输入你要修改学生的学号:')
        i=0
        leap=0
        for temp in s:
            if temp['id']==alterId:
                leap=1
                break
            else:
                i=i+1
        if leap==1:
            while True:
               alterNum=int(input('1.修改学号\n 2.修改姓名\n 3.修改年龄\n 4.修改学科\n 5.修改分数\n 6.退出修改\n-'))
               if alterNum==1:
                   newId=input('输入更改后的学号:')
                   i = 0
                   leap1=0
                   for temp1 in s:
                        if temp1['id']==newId:
                            leap1=1
                            break
                        else:
                            i=i + 1
                   if leap1==1:
                    print('输入学号不可重复，修改失败！')
                   else:
                    temp['id']=newId
                    print('学号修改成功')
               elif alterNum==2:
                    newName=input('输入更改后的姓名:')
                    temp['name']=newName
                    print('姓名修改成功')
               elif alterNum==3:
                    newAge=input('输入更改后的年龄:')
                    temp['age']=newAge
                    print('年龄修改成功')
               elif alterNum==4:
                    newObject=input('请输入更改后的学科')
                    temp['object']=newObject
                    print('科目修改成功')
               elif alterNum==5:
                    newScore=input('请输入更改后的分数')
                    temp['score']=newScore
                    print('分数更改成功')
               elif alterNum==6:
                    break
               else:
                    print('输入错误请重新输入')
        else:
            print('没有学号，修改失败！')

    elif key==4:
        print('你选择了查询学生信息功能')
        print('*' * 20)
        print('接下来进行遍历所有的学生信息……')
        print('id      姓名     年龄     学科       分数')
        for temp in s:
            print('%s    %s    %s    %s    %s' % (temp['id'], temp['name'], temp['age'],temp['object'],temp['score']))
        print('*' * 20)
        searchID=input('请输入你要查询学生的学号:')
        i=0
        leap=0
        for temp in s:
            if temp['id']==searchID:
                leap=1
                break
            else:
                i=i+1
        if leap==0:
            print('没有此学生号，查询失败！')
        else:
            print('找到此学生，信息如下：')
            print('学号:%s\n姓名:%s\n年龄:%s\n学科:%s\n分数:%s\n' % (temp['id'],temp['name'],temp['age'],temp['object'],temp['score']))
    elif key == 5:
        s = sorted(s, key=lambda temp: temp["score"],reverse = True)
        print (s)
    elif key==6:
        quitconfirm=input('亲，真的要退出吗（yes 或者 no）')
        if quitconfirm =='yes':
            print('欢迎使用本系统，谢谢')
            break
    else:
        print('您输入有误，请重新输入')
