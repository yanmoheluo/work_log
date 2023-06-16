
# GIT分支使用及开发要求说明
# 一.技术开发要求
   ## 注意：要求测试用例要在代码review之前完成
# 二.关于git 的使用
    以后严格要求如下：每个人必须有以下分支概念，并且要严格执行
                  1.master 分支 （客户运营分支-长期存在分支） 客户线上运行主分支
                  2.daigou/develop/release/dev 分支  预发布分支（测试分支-长期存在分支-release预发布分支） 线上网站测试分支
                  3.feature_xxx_yymmdd  开发分支(自己的开发分支-开发期间存在的分支)
                          每个网站必须有每个网站的本地功能分支进行开发
                  4.hotfix_xxx_yymmdd 修改bug 分支  (自己的开发分支-开发期间存在)
# 三.关于自建的开发分支命名规则要求：
       1.要区分是功能分支还是修复bug的分支
       2.功能分支主要指 客户网站开发，新增模块开发，客户要求修改的一下小问题。。。。
             命名规则：feature_xxx_yymmdd  feature 固定的
       3.bug 分支 主要指 bug修复的分支  举例：如加入购物车数量错误了，调整了一下
            命名规则：hotfix_xxx_yymmdd：
            注意：yymmdd为拉取出hotfix的日期，一般情况下hotfix的bug必须当天修复、发布。
# 四.仓库分支说明

# 五.代码review
       提交合并请求前注意：
       例如我要将我的 feature_order_create_20221116 分支合并到 预发布分支 dev
           执行操作：我当前所处分支为 feature_order_create_20221116
              git checkout dev
              git pull origin dev
              git checkout feature_order_create_20221116
              git merge dev  (这个注意解决冲突)
              git push origin feature_order_create_20221116 (如果有冲突先git pull 解决冲突正常应该不会有冲突才对)
              然后执行 代码review
              最后删除 feature_order_create_20221116
              在git.zzqss.cn:99 上直接删除也是可以的
              本地执行命令 git push origin --delete feature_order_create_20221116

              代码review 说明
              https://www.cnblogs.com/lufei910/p/14736076.html?share_token=e6776f2c-5926-4879-ab51-7ac7cb91f966
              我们做代码review提交信息主要注意 两行整一下即可
              【标题行】 必填, 描述主要修改类型和内容。
              【主题内容】 描述为什么修改, 做了什么样的修改, 以及这么做的思路等等。
              git  Commit 提交要求加一下下面几个前缀：
              feature：新特性
              hotfix：修改 bug
              refactor：代码重构
              style：代码格式修改
              release:预发布分支 发布正式版
              test：测试用例修改
              chore：其他修改, 比如构建流程, 依赖管理
              示例：git commit -m 'feature 积分功能‘
                     git commit -m 'hotfix 查询订单列表’
