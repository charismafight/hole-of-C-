# .net调用webservice的总结
由于需要设计对于各种接口方式的通用框架，也重新记录一遍.net下ws的细节。webservice比较重要的信息都在wsdl文件中，所以只需要配置好service的url，然后给它加上wsdl后缀获取到服务的配置信息。


想要动态的调用ws，可以考虑拼接http或是soap请求，但这种实现过于繁琐，需要编写大量拼接的内容，尤其是soap协议。另一种方法可以用工具生成wsdl文件，然后修改源码
调用（修改调用函数+参数，优势是不需要操心ws约定，生成完毕后写代码调用方法完事，但缺点是太不灵活）。

最后还可以写动态代理类来处理ws请求，调用方可以直接提供参数的hashtbale和url，但如何处理返回值是个问题。

返回值的问题可以考虑统一返回一个xml字符串，然后使用xslt来解析出通用的xml进一步来实现代理效果。这样的优势在于只需要定义好当前系统中要调用外部ws的接口需要什么格式的返回xml即可，保证了解耦效果。