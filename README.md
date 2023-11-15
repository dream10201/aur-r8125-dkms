# root用户
vi /usr/bin/makepkg
//搜索OPT_LONG
//添加 'asroot'
//搜索EUID
EUID == 1
# 编译
makepkg -f

# 安装
makepkg -si
