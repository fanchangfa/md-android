请介绍下ContentProvider是如何实现数据共享的。
一个程序可以通过实现一个Content provider的抽象接口将自己的数据完全暴露出去，而且Content providers是以类似数据库中表的方式将数据暴露。Content providers存储和检索数据，通过它可以让所有的应用程序访问到，这也是应用程序之间唯一共享数据的方法。
要想使应用程序的数据公开化，可通过2种方法：创建一个属于你自己的Content provider或者将你的数据添加到一个已经存在的Content provider中，前提是有相同数据类型并且有写入Content provider的权限。
如何通过一套标准及统一的接口获取其他应用程序暴露的数据？
Android提供了ContentResolver，外界的程序可以通过ContentResolver接口访问ContentProvider提供的数据。