# KUAIDI-
互联网+项目快递一公里
连接后台需要统一一下appid：wxa1b202ae01b354d3
所有返回是，否等判断信息的接口，均为1为成功，0为失败,-1为错误码，对应名称为code

后台接口信息：
-------------用户部分-------------------

**用户登录：login
必传参数：
  *identiy:用户身份信息，1为农户，2为车主
  *code：用户生成的sessionID
返回值：
  *code
  *user:用户信息

**用户注册：register
必传参数：
  *code：用户生成的sessionID
  *identify：用户身份信息，1为农户，2为车主
  *name：用户姓名
  *number：身份证号
  *telephone：电话
可选参数：
  *sex：性别
  *age：年龄
返回值：
  *code

**用户身份证信息验证：idnumber
必传参数：
  *idnumber：用户身份证信息号码
返回值：
  *idreal：1真，0假
/*这里建议做一下异步通讯，在输入号码的时候自动进行查询，如果号码为假则无法进行注册*/
-----------------订单部分-----------------

**农户查询订单：selfarinfo
必传参数：
  *status：查询订单类型，0为正在进行中订单，1为历史记录
返回值：
  *info：用户订单信息list
  *code：1，-1

**车主查询进行中订单：selcarinfo
返回值：
  *info：订单信息
  *code：1，-1

**车主查询未进行订单（未接单）：selallinfo
返回值：
  *info：所有未进行订单list

**农户发布订单：addinfo
必传参数：
  *text：标题
  *goods：货物信息
  *weight：重量
可选参数：
  *message：留言
返回值：
  *code

**车主端更新车主位置信息（判断是否取消订单）：updlocal
必传参数：
  *longitude：经度
  *latitude：纬度
返回值：
  *code：1成功，0为订单已取消

**农户获取车主位置：getlocal
必传参数：
  *id：订单对应的id号
返回值：
  *latitude：纬度
  *longitude：经度

**车主接单：addcarer
必传参数：
  *longitude：经度
  *latitude：纬度
  *id：要接的单对应的id号
返回值：
  *code：
    =1:接单成功
    =0：接单失败，已有正在进行中订单
    =-1：未知错误

**完成订单（农户端）：comfarinfo
必传参数：
  *id：需要结束的订单id
返回值：
  *validcode：验证码，司机端输入
  *code：1，-1

**完成订单（车主端）：comcarinfo
必传参数：
  *validcode:由农户处获取的验证码
返回值：
  *code：
    =1：订单完成
    =0：验证码错误
    =-1：未知错误

**农户取消订单：delfarinfo
必传参数：
  *id：需要取消的订单id
返回值：
  *code：1，0

**车主取消订单：delcarinfo
必传参数：
  *id：需要取消的订单id
返回值：code：1，0
