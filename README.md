# Beginner-s-Exercises---Department-of-Library-Management
初学者的一次联系，参考csdn上的创作者——以山河作礼

#代码：
class Library():
    """图书管理系统"""
    def __init__(self):
        self.book={}
        while True:
            print("1：图书添加  2：图书删除 3：图书位置修改 \n "
                  "4：图书借出  5：图书还回 6：图书信息查看  7：退出系统")
            func_code = input("请您输入需要是使用的功能：")
            if func_code == "1":
                self.add_book()
            elif func_code == "2":
                self.del_book()
            elif func_code == "3":
                self.modify_book()
            elif func_code == "4":
                self.lend_book()
            elif func_code == "5":
                self.give_back()
            elif func_code == "6":
                self.select_book()
            elif func_code == '7':
                break
            else:
                print("输入的选项id无效！")


    def add_book(self):
        """添加书籍信息"""
        book_name=input("输入book'name: ")
        book_id=input("输入book'id: ")
        book_id=int(book_id)
        book_position=input("输入书的位置： ")
        is_lend = False
        self.book[book_name]={
            'book_id': book_id,
            'is_lend':is_lend  ,
            'book_position':book_position
        }
        print("书籍信息添加完成")

    def del_book(self):
        """删除书籍信息"""
        book_name=input("你想删除的书籍的名称：")
        del self.book[book_name]
        print("书籍信息已删除")
    def select_book(self):
        book_name=input("你要查找的书籍：")
        if book_name in self.book:
            if self.book[book_name]['is_lend']:
                print("书已被借出")
            else :
                print("书籍在"+self.book[book_name]['book_position'])
        else:
            print("很抱歉，馆内无此书")

    def modify_book(self):
        book_name=input("输入你要改变位置的书籍")
        self.book[book_name]['position']=input("输入更改后的位置： ")
        print("位置已修改完成，%s现在在%s"%(self.book[book_name],self.book[book_name]['book_position']))

    def lend_book(self):
        book_name=input("输入你想借的书：")
        self.book[book_name]['is_lend']=True
        print("借书成功")

    def give_back(self):
        book_name=input("输入您要换的书")
        self.book[book_name]['is_lend'] = False

t=Library()
