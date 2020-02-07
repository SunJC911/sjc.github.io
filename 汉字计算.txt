def trans_to_nums(cn):
	if cn == "零":
		return 0
	elif cn == "一":
		return 1
	elif cn == "二":
		return 2
	elif cn == "三":
		return 3
	elif cn == "四":
		return 4
	elif cn == "五":
		return 5
	elif cn == "六":
		return 6
	elif cn == "七":
		return 7
	elif cn == "八":
		return 8
	elif cn == "九":
		return 9
	elif cn == "十":
		return 10
	else:
		print(cn+"不是零到十之间的数字！重启吧！")


def trans_to_cn(num):
	if num == 0:
		return "零"
	elif num == 1:
		return "一"
	elif num == 2:
		return "二"
	elif num == 3:
		return "三"
	elif num == 4:
		return "四"
	elif num == 5:
		return "五"
	elif num == 6:
		return "六"
	elif num == 7:
		return "七"
	elif num == 8:
		return "八"
	elif num == 9:
		return "九"
	elif num == 10:
		return "十"
	else:
		print(num+"不是0到10之间的数字！重启吧！")


print("输入数字应属于非负整数，没输入语句时按回车退出，发生错误会自动退出。")
try:
	names = {}  # 用字典存放变量名及对应变量值
	while True:  # 用死循环来变得像交互式
		no = input()  # 装入语句
		if no is "":  # 没输入语句时按回车退出
			exit()
		if no.split()[0] == "整数":  # 针对“整数”开头的定义语句
			names[no.split()[1]] = trans_to_nums(no.split()[3])  # 装入变量名及对应变量值
		elif no.split()[0] in names.keys():  # 针对“变量名”开头的操作语句
			if no.split()[1] == "减少":
				names[no.split()[0]] -= trans_to_nums(no.split()[2])
			elif no.split()[1] == "增加":
				names[no.split()[0]] += trans_to_nums(no.split()[2])
			elif no.split()[1] == "乘以":
				names[no.split()[0]] *= trans_to_nums(no.split()[2])
			elif no.split()[1] == "除以":  # 讨论除数为0，除后结果为小数
				if trans_to_nums(no.split()[2]) == 0:
					print("除数不能为零，请重新输入语句！")
				else:
					a = names[no.split()[0]] / trans_to_nums(no.split()[2])
					if a is not int:
						while True:
							print("运算结果为小数，输入“还原”变回原数值，输入“继续”则将强制转换成整数：")
							b = input()
							if b == "还原":
								break
							elif b == "继续":
								names[no.split()[0]] = int(a)
								break
					else:
						names[no.split()[0]] = a
		elif no.split()[0] == "看看":  # 输出指定变量值
			print(trans_to_cn(names[no.split()[1]]))
		elif no.split()[0] == "如果":  # 分多种讨论
			if no.split()[2] == "大于":  # 判断是否大于
				if names[no.split()[1]] > trans_to_nums(no.split()[3]):  # “则”后的操作语句
					if no.split()[5] == "看看":
						print(no.split()[6][1:-1])
					else:
						if no.split()[6] == "增加":
							names[no.split()[5]] += trans_to_nums(no.split()[7])
						elif no.split()[6] == "减少":
							names[no.split()[5]] -= trans_to_nums(no.split()[7])
						elif no.split()[6] == "乘以":
							names[no.split()[5]] *= trans_to_nums(no.split()[7])
						elif no.split()[6] == "除以":
							if trans_to_nums(no.split()[7]) == 0:
								print("除数不能为零，请重新输入语句！")
							else:
								a = names[no.split()[5]] / trans_to_nums(no.split()[7])
								if a is not int:
									while True:
										print("运算结果为小数，输入“还原”变回原数值，输入“继续”则将强制转换成整数：")
										b = input()
										if b == "还原":
											break
										elif b == "继续":
											names[no.split()[5]] = int(a)
											break
								else:
									names[no.split()[5]] = a
				else:  # “否则”后的操作语句
					if no.split()[8] == "看看":
						print(no.split()[9][1:-1])
					elif no.split()[8] == "无":
						pass
					elif no.split()[9] == "无":
						pass
					elif no.split()[9] == "增加":
						names[no.split()[8]] += trans_to_nums(no.split()[10])
					elif no.split()[9] == "减少":
						names[no.split()[8]] -= trans_to_nums(no.split()[10])
					elif no.split()[9] == "乘以":
						names[no.split()[8]] *= trans_to_nums(no.split()[10])
					elif no.split()[9] == "除以":
						if trans_to_nums(no.split()[10]) == 0:
							print("除数不能为零，请重新输入语句！")
						else:
							a = names[no.split()[8]] / trans_to_nums(no.split()[10])
							if a is not int:
								while True:
									print("运算结果为小数，输入“还原”变回原数值，输入“继续”则将强制转换成整数：")
									b = input()
									if b == "还原":
										break
									elif b == "继续":
										names[no.split()[8]] = int(a)
										break
							else:
								names[no.split()[8]] = a
					elif no.split()[9] == "看看":
						print(no.split()[10][1:-1])
					elif no.split()[10] == "增加":
						names[no.split()[9]] += trans_to_nums(no.split()[11])
					elif no.split()[10] == "减少":
						names[no.split()[9]] -= trans_to_nums(no.split()[11])
					elif no.split()[10] == "乘以":
						names[no.split()[9]] *= trans_to_nums(no.split()[11])
					elif no.split()[10] == "除以":
						if trans_to_nums(no.split()[11]) == 0:
							print("除数不能为零，请重新输入语句！")
						else:
							a = names[no.split()[9]] / trans_to_nums(no.split()[11])
							if a is not int:
								while True:
									print("运算结果为小数，输入“还原”变回原数值，输入“继续”则将强制转换成整数：")
									b = input()
									if b == "还原":
										break
									elif b == "继续":
										names[no.split()[9]] = int(a)
										break
							else:
								names[no.split()[9]] = a

			if no.split()[2] == "小于":  # 判断是否小于
				if names[no.split()[1]] < trans_to_nums(no.split()[3]):  # “则”后的操作语句
					if no.split()[5] == "看看":
						print(no.split()[6][1:-1])
					else:
						if no.split()[6] == "增加":
							names[no.split()[5]] += trans_to_nums(no.split()[7])
						elif no.split()[6] == "减少":
							names[no.split()[5]] -= trans_to_nums(no.split()[7])
						elif no.split()[6] == "乘以":
							names[no.split()[5]] *= trans_to_nums(no.split()[7])
						elif no.split()[6] == "除以":
							if trans_to_nums(no.split()[7]) == 0:
								print("除数不能为零，请重新输入语句！")
							else:
								a = names[no.split()[5]] / trans_to_nums(no.split()[7])
								if a is not int:
									while True:
										print("运算结果为小数，输入“还原”变回原数值，输入“继续”则将强制转换成整数：")
										b = input()
										if b == "还原":
											break
										elif b == "继续":
											names[no.split()[5]] = int(a)
											break
								else:
									names[no.split()[5]] = a
				else:  # “否则”后的操作语句
					if no.split()[8] == "看看":
						print(no.split()[9][1:-1])
					elif no.split()[8] == "无":
						pass
					elif no.split()[9] == "无":
						pass
					elif no.split()[9] == "增加":
						names[no.split()[8]] += trans_to_nums(no.split()[10])
					elif no.split()[9] == "减少":
						names[no.split()[8]] -= trans_to_nums(no.split()[10])
					elif no.split()[9] == "乘以":
						names[no.split()[8]] *= trans_to_nums(no.split()[10])
					elif no.split()[9] == "除以":
						if trans_to_nums(no.split()[10]) == 0:
							print("除数不能为零，请重新输入语句！")
						else:
							a = names[no.split()[8]] / trans_to_nums(no.split()[10])
							if a is not int:
								while True:
									print("运算结果为小数，输入“还原”变回原数值，输入“继续”则将强制转换成整数：")
									b = input()
									if b == "还原":
										break
									elif b == "继续":
										names[no.split()[8]] = int(a)
										break
							else:
								names[no.split()[8]] = a
					elif no.split()[9] == "看看":
						print(no.split()[10][1:-1])
					elif no.split()[10] == "增加":
						names[no.split()[9]] += trans_to_nums(no.split()[11])
					elif no.split()[10] == "减少":
						names[no.split()[9]] -= trans_to_nums(no.split()[11])
					elif no.split()[10] == "乘以":
						names[no.split()[9]] *= trans_to_nums(no.split()[11])
					elif no.split()[10] == "除以":
						if trans_to_nums(no.split()[11]) == 0:
							print("除数不能为零，请重新输入语句！")
						else:
							a = names[no.split()[9]] / trans_to_nums(no.split()[11])
							if a is not int:
								while True:
									print("运算结果为小数，输入“还原”变回原数值，输入“继续”则将强制转换成整数：")
									b = input()
									if b == "还原":
										break
									elif b == "继续":
										names[no.split()[9]] = int(a)
										break
							else:
								names[no.split()[9]] = a
		else:
			print("请输入正确开头！")
except IndexError:
	print("你为什么不好好输入句子？")
except TypeError:
	print("你为什么不好好输入数字？")
except SystemExit:
	print("拜拜！")
