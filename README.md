# Cesium_trainlog_WuShaoWen
# 学习记录

## 有道云笔记
<!-- 标题+内容 列出所有的笔记
* [这个GitHub页面](https://github.com/snowflowersnowflake/Cesium_trainlog_WuShaoWen/edit/main/README.md) -->
* [自行运行代码与实现效果部分] https://note.youdao.com/noteshare?id=a0774737cd35d6d901aad07c74445e84
* [每日问题收集(未解决)] https://note.youdao.com/s/B57GNMwY

## 问答整理
学习问题和记录整理到这
* 问题1：cesium内的坐标系是什么原理
* 回答:笔记地址 https://note.youdao.com/s/6ZvLE9Pz
* 问题2: glb是什么文件格式,原理
* 回答 笔记地址 https://note.youdao.com/noteshare?id=8e6799d20a81912d43a4f39a8ea0e478
* 问题2的追问2: 如何避免gltf文件变大
* 回答:笔记地址 https://note.youdao.com/noteshare?id=0150d2e1e77cf0031e47aa0ea2b11593
* 问题2的追问2: glb文件索引引入原理
* 回答: 笔记地址 https://note.youdao.com/s/C8PEpILC
* 问题2的追问3: accessor对象怎么实现的？
* 回答: 笔记地址 https://note.youdao.com/s/5icsNwaN
* 问题二的追问3: float类型数据结构最大表示几位
* 回答: https://note.youdao.com/noteshare?id=3fb8a86cd366ef372a40d5d6e551c6eb
* 问题二的追问4 向量化为什么可以减少gltf体积
* 回答: https://note.youdao.com/s/5zqjCdx
* 问题3：cesium有哪几种颜色格式？
* 1.cesium默认的几种:如Cesium.Color.RED 
* 2.16进制颜色设置 如:Cesium.Color.fromCssColorString('#67ADDF') 
* 3.rgba 如:Cesium.Color(1,0.1,0.5,0.5) 4.随机颜色 Cesium.Color.fromRandom()
* 问题4：如何改变cesium中的颜色？
* 1.primitive的纹理属性material>uniform>color 来控制颜色 2.entity 中的color控制颜色 如:添加model时,entity.model.color = Cesium.Color.fromRandom();
* 问题5: 材质material的原理
* 回答: Cesium中的Material类的内部机制是通过一种json格式的Fabric对象来表达物体的外观特征，而这些外观特征是由漫反射(diffuse)、镜面反射(specular)、法向量(normal)、自发光(emission)以及透明度（alpha）组合（即一个Components）而成
* 问题6: 材质material设置的几种方式
* 回答: https://note.youdao.com/s/1LulXNed
* 问题7: 什么是顶点着色器,片元着色器,有哪些方法?
* 回答:
* 问题8: cesium控制相机的几种方式
* 回答: https://note.youdao.com/s/b84diA4W

## 实战案例
* 1.cesium主题,控件展示,只需要根据属性控制是否展示
* https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/index.vue
* 2.不同精度DEM合并
* 工具使用,暂不处理
* 3.cesium 地球改为其他纯色
* https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/index_color.vue
* 4.cseium 视角转换
* https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/visualFly.vue
* 5.节省性能
* (1).可用viewer.scene.debugShowFramesPerSecond = true; 展示当前fps帧率;
* (2).viewer.resolutionScale =0.9; 调整画面精细度 默认1.0 
* (3). 3DTiles 相关设置 maximumScreenSpaceError:64 //默认值16 用于判断当前层级上的三维碎片是否显示 ,值越大,显示地形越少
* (4).画面不变化时,停止渲染 (初始化时requestRenderMode : true, 或者  viewer.scene.requestRenderMode = true
* 6.气泡窗口  额外添加html节点显示信息 防遮挡
* 将世界坐标转化为屏幕坐标然后赋值  https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/index.vue
* 7.禁止摄像头进入地底
* 尝试之后发现,目前的版本貌似不能进入地底
* 8.修改选择指示器的样式
* 基本的js选择dom修改,不描述
* 9.展示自己的glb文件
* https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/index_glb.vue.
* 10.使用GUI控件
* 相当于ui组件库,自己也可以做 略过
* 11.entities与Primitive绘制管线
* https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/primitiveORentities.vue
* 12.限制底图显示范围
* addImageryProvider添加底图时 rectangle:Cesium.Rectangle.fromDegrees(0,0,117,32),//最小纬度,.最小经度,最大纬度,最大经度 设置范围
* 13.创建自定义形状
* ×××(未完成)用GeometryAttribute函数自己定义了一个四边形,坐标顶点信息自己定义的,但是到渲染那一步出现问题了,卡着没做出来,变换矩阵一直有问题
* 14.cesium与three.js结合使用
* ×××(未完成)
* 15.osgb转3Dtiles
* 工具使用,暂不处理
* 16.射线ray
*  通过pick方法获取到世界坐标 或者是 primitive对象 https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/pick3Dtileset.vue
* 17.获取离线地图
* 暂时使用线上地址,暂不处理
* 18.自定义搜索控件
* 内置的为 发送请求到api.cesium.com/v1/geocode/autocomplete 查询数据,如需要也可以自己添加dom处理查询,暂不处理
* 19.3Dtiles旋转问题
* 暂不知道是什么问题,暂不处理
* 20.水面效果
* https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/waterRipple.vue
* 21.动态改变材质
* https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/changeMaterial.vue
* 22.entity和primitive 画矩形或者线 动态纹理
* https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/dynamicTexture.vue

## 其他
暂时完成上面的部分

## 打卡 (表示已完成当天学习计划)
* [✔] 2022/4/22 
* [✔] 2022/4/23 
* [✔] 2022/4/24 
* [✔] 2022/4/25
*  1.地图底色改变 示例 2.视角移动 示例 3.entities模型移动位置 示例
* 1.https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/index_color.vue
* 2.https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/visualFly.vue 
* 3.https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/modalFly.vue 
* [✔] 2022/4/26
* 添加气泡窗口 使用html节点,世界坐标转换为屏幕坐标 https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/index.vue
* 节省性能的一些方法
* 加载wmts瓦片,加载天地图http://t0.tianditu.com/cva_w/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=cva&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles&tk=9669a91e46fd2e29bbbc8cf5130caebc  LAYER参数与前面的要同步修改,不然请求不到数据
* [✔] 2022/4/27
* 1.entities绘制面添加 图片材质 2.entities与Primitive绘制管线 https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/primitiveORentities.vue
* [✔] 2022/4/28
* 添加水波纹效果,全球或局部位置 https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/waterRipple.vue
* 2022/4/29 
* 1.通过pick方法获取到世界坐标 或者是 primitive对象 https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/pick3Dtileset.vue
* 2.自定义形状矩形  未完成

* [✔]2022/5/9
* 1.动态改变材质 https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/changeMaterial.vue
* 2.primitive和entity 画矩形或者线 动态纹理  https://github.com/wusjaowen/cesium-dome/blob/main/src/page/login/dynamicTexture.vue

* [✔]2022/5/12
* 问题5: 材质material的原理 问题6: 材质material设置的几种方式


## 困难记录
2022.5.9:

1.cesium构建自定义形状的矩形,用GeometryAttribute函数自己定义了一个四边形,坐标顶点信息自己定义的,但是到渲染那一步出现问题了,卡着没做出来,变换矩阵一直有问题

2.cesium和three.js结合使用,分开渲染是没问题的,结合起来使用目前还没实现

3.加载飞机模型,如果高度低了可能会卡进地底这个问题,不知道是否是框架问题
