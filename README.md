# Railway_Kiwiland
Railway_Kiwiland
#程序所解决的问题:
1.计算站点组成的路线距离值
2.计算两个站点之间最短路径长度
3.计算循环线路路程小于M的所有可行线路
4.计算行程数最多为N站是所有可行的线路
5.计算行程数恰好为N站是所有可行的线路
#程序思路:
站点与站点之间的关系满足有向图这种数据结构,同时结合实际的情况来看还存在环(以某个站点为起始点通过错综复杂的线路走法又会绕回该站点)。首先将站点,站点与站点的之间的距离通过图的一般存储方式(邻接矩阵 邻接表等),当前实现了邻接矩阵和邻接表这两种方式。
将需要解决的问题进行分类归,溯本求原,最核心的功能需要解决,当已知一个起始站点和一个终止站点后,可以列出所有能可行的线路,等价于得到中途会经过那些站点(每条线路中最多只包含一个可以构成环的可能性)。
将问题分类后决定选择单例的方式来初始化所有处理具体某类问题的对象,而且所有的这些对象都继承同一个父类,实现同一个接口,这样设计的原因主要是因为前面所总结出的结论,解决所有问题的第一步还是需要得出起始和终止站点所有可行线路(每条线路中最多只包含一个可以构成环的可能性),当获得这个结果集后,就根据具体问题的具体特质来处理,自然而然就可以将处理方法定义成一个抽象方法,然后去依次实现。采用这种抽像工厂的模式为了后期扩展如果需要解决一类的新的问题时,只需要直接实现抽像方法即可。
#程序运行方式说明:
1.程序的启动入口为:
com.howard.www.railway.boot包中的RailwayNetworkBoot类main方法
#具体类说明:
核心:遍历站点根据一个起始站点和一个终止站点,获取所有能可行的线路,得到中途会经过那些站点
在com.howard.www.railway.calculation包中,BaseCalculationRouteSite类的obtainRouteSite方法。
com.howard.www.railway.calculation包中CalculationSpecifiedRouteDistance类,计算站点组成的路线距离值
com.howard.www.railway.calculation包中CalculationMinimumRouteDistance类,计算两个站点之间最短路径长度
com.howard.www.railway.calculation包中CalculationCircleRouteDistance类,计算循环线路路程小于M的所有可行线路
com.howard.www.railway.calculation包中CalculationMostRouteDistance类,计算行程数最多为N站是所有可行的线路
com.howard.www.railway.calculation包中CalculationJustRightRouteDistance类,计算行程数恰好为N站是所有可行的线路
#收获:
加深了对图这种数据结构的认识,最主要的是知道了它的存储方式和实现,学习了佛洛依德最短距离算法,开发过程中遇到的问题是在遍历时因为涉及到了递归,所有在判断出错就会循环调用,抛出stackoverflowerror,在思考的过程中主要通过先在纸上通过画图的方式,构思好实现的逻辑。花费时间最多的地方就是计算循环线路路程小于M的所有可行线路、计算行程数最多为N站是所有可行的线路、计算行程数恰好为N站是所有可行的线这三个问题。在程序中确实用了很多的嵌套for循环,当前还是没有想到好的办法,但是这个问题还是会一直去进行优化的,多借鉴一些比较好的设计,逐步优化。
