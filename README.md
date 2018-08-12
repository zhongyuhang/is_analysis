# 迷宫
|学校|专业|姓名|邮箱|
|:-------:|:-------------: | :----------:|:-------------: |
|成都大学|软件工程(本)15-2|钟宇航|18990051970@163.com|
## 单元测试：没有。。
### 代码
``` python
"""
因为星期六加班了。。只有星期天半天的时间来搞了这个，谢谢将就到看下吧。。。
"""
class maze():
	# 获取迷宫的尺寸，返回没有打通通道的迷宫
	def getMaze(self, *par):
		maze = []
		dfs = [['[W]' for col in range(par[0] * 2 + 1)] for row in range(par[1] * 2 + 1)]
		x = [x for x in range(len(dfs)) if x % 2 == 0 and x != 0]
		y = [y for y in range(len(dfs[1])) if y % 2 == 0 and y != 0]
		for i in x:
			for j in y:
				dfs[i - 1][j - 1] = '[R]'
		return dfs

	# for k in range(len(dfs)):
	# 	print(dfs[k])
	# 每次yield返回两个连接的点
	def mazeRoda(self, data):
		for eachroad in data.split(';'):
			fistr = str(eachroad).split(' ')
			point_1 = fistr[0].split(',')
			point_2 = fistr[1].split(',')
			x = [(int(x) + 1) * 2 - 1 for x in point_1]
			y = [(int(y) + 1) * 2 - 1 for y in point_2]
			yield x, y


data = "0,1 0,2;0,0 1,0;0,1 1,1;0,2 1,2;1,0 1,1;1,1 1,2;1,1 2,1;1,2 2,2;2,0 2,1"
a = maze()
dfs = a.getMaze(3, 3)
for i in a.mazeRoda(data):
	if i[0][0] == i[1][0]:
		length = i[0][0]
		width = int((i[0][1] + i[1][1]) / 2)
		dfs[length][width] = '[R]'
	if i[0][1] == i[1][1]:
		length = int((i[0][0] + i[1][0]) / 2)
		width = i[0][1]
		dfs[length][width] = '[R]'
for i in range(len(dfs)):
	print(dfs[i])
```
