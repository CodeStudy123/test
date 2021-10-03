# 初始化本地库
# git init 
  会生成一个隐藏的.git目录，存放本地库相关的目录和文件


# 设置签名（项目/仓库级别）
# git config user.name <name> 
# git config user.email <email>
  代表开发人员的身份，加--global表示系统用户级别
  优先级：项目/仓库 > 系统用户 两者都没有是不被允许的


# git status 
  查看工作区、暂存区状态
  显示红色：工作区与暂存区不一致、提示你add or/and commit
  显示绿色：工作区与暂存区一致，但是与本地库不一致，提示你commit
  不显示东西：工作区、暂存区、本地库都一致
# git add <file>
  将工作区的新建/修改添加到暂存区
# git commit -m 'commit.message' <file> 
  将暂存区的的内容提交到本地库
  新建文件除外：当修改了工作区时，可以直接commit而不用add它内部会帮我们做


# 版本的历史记录，每次提交本地库都会产生一次记录
# git log 
  显示日志
# git log --oneline 
  以一行显示，且只会显示当前指向的版本及它之前的版本，如果后退就看不到之后的了
# git reflog 
  会显示移动到目标版本需要多少步，会显示所有版本 HEAD@{0}：最新版本


# 前进和后退
# git reset --hard 局部索引值
  依据索引值
# git reset --hard HEAD^/HEAD~数字 
  依据HEAD指针后退，^的数量 or ~数字=决定后退几步   ^^^^===~4
# reset后面的三种参数：
# --hard :移动HEAD指针、重置暂存区、重置工作区 文件删除找回就是利用的这个特性
# --mixed :移动HEAD指针、重置暂存区
# --soft :只移动HEAD指针


# 文件删除的找回： 前提：文件曾commit过
# rm 文件名 
  删除工作区的文件
# 当工作区文件删除时：
  1、（文件的删除）修改操作已经commit：利用--hard回退上一步
  2、（文件的删除）修改操作没有commit：直接 git reset --hard HEAD


# 文件比较：
# git diff 文件名
  把工作区的文件与暂存区比较
# git diff HEAD^ 文件名
  把工作区的文件与本地库历史的前一个版本的文件比较

# 分支操作：
# git branch -v 
  查看当前有多少分支，以及分支所对应的版本
# git brabch 分支名 ：创建分支
# git checkout 分支名 ：切换分支
# git merge 分支名 ：合并分支到当前分支
# 产生冲突时：两个分支父级是同一个版本，两个分支都提交了，vim 文件修改成想要的样子，再add、commit（不加文件名）