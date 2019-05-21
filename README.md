# -20185111040-
#利用百度文字识别引擎识别网络图片文字
MyPath = ")E:\\python\\xxxxx\\"#这是读取的图片存放的文件夹的路径，可以改为要读取的文件夹
filesoure = MyPath
def baiduduqu(filesoure,filename):
	from aip import AipOcr
	import re
	import os
	APP_ID = 'xxxx'
	API_KEY = 'xxxxx'
	SECRET_KEY = 'xxxx'
	client = AipOcr(APP_ID, API_KEY, SECRET_KEY)
	dakai = open(filename,'rb')
	duqu = dakai.read()
	message = client.basicGeneral(duqu)
	for duqu in message.get('words_result'):
		print(duqu.get('words'))
 
def filename (fielsoure,filetype):
	import os
	pathDir = os.listdir(filesoure)
	for allDir in pathDir:
		child = os.path.join('%s%s' % (filesoure,allDir))
		print(child)
		baiduduqu(filesoure,child)
def run():
	import os
	os.chdir(filesoure)
	for i in os.listdir(os.getcwd()):
		postfix = os.path.splitext(i)[1]
		if postfix == '.jpeg' or postfix == '.png':
			filename(filesoure,postfix)
 
if __name__ == '__main__':
   run()
