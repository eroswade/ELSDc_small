cmake_minimum_required (VERSION 2.8)
# 项目信息
project (ELSDc)
# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)# 把当前文件夹下的所有源文件存到DIR_SRCS变量
add_executable(ELSDc main.c ${DIR_SRCS})

find_package(lapack) # 找外部库
if (LAPACK_FOUND) # 如果找到了
  include_directories(${LAPACK_INCLUDE_DIRS}) #包含库路径
  target_link_libraries (ELSDc ${LAPACK_LIBRARIES} ) # link的时候导入库
endif (LAPACK_FOUND)