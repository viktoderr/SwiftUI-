# SwiftUI-
SwiftUI的学习
SwiftUI
	SwiftUI 教程
		1 SwiftUI基础
			一 创建和组合视图
				目的：这个教程指导你构建一个名为Landmarks(地标)的应用。这个应用的功能是可以发现并分享你喜欢的地标。首先从创建地标详情页开始。\n\n准备：Landmarks使用栈来按层组合图片、文本等视图元素，从而布局页面。在视图中添加地图，需要引入MapKit(地图套件)组件，在你布局页面的过程中， Xcode可以提供实时的反馈，让你所做的改动立即转化成对应的代码实现。
					检查是否理解
						协议相当于接口
						
							
								
							
								解答：水平栈HStack排除A选项，先声明CirleImage（）即先出现圆形图标，排除B选项，标题字样为“Turtle Rock”
						
							
								解答：Divider=分割线,文本视图存在于VStack中，排除B选项，C选项不符合Swift语法排除。
							
								
						
							
								
							
								解答：语法格式为.foregroundColor(.purple),排除A，B选项。\n前景颜色（.紫色）= .foregroundColor(.purple)
								修改器每次都是返回一个新的对象，所以多个修改器可以通过链式调用
				第一节 创建新项目并体验画布
					任务：创建SwiftUI项目工程，体验画布、预览模式和SwiftUI模板代码\n\n注意：要想在Xcode中预览画布中的视图或者与画布中的视图进行交互，要求你的Mac系统版本号不低于macOS Catalina 10.15（10.15.7 (19H1922)）
						
							
					步骤
						步骤1 打开Xcode，在启动页面点击创建新工程或者在菜单中选择文件->新建->项目\n\n
							
						步骤2 在项目模板选择器中，选择iOS作为项目平台，选项单视图应用(Single View App)作为项目模板，并点击下一步(Next)
							
							没有单视图应用这个选项，我选择的是App这个选项
						步骤3 输入Landmarks作为项目名称，选择SwiftUI作为用户界面的创建方式，并点击下一步(Next)，在磁盘目录下选择一个位置用来存放新创建的工程项目
							
							
							位置
						步骤4 工程创建好并打开后，在文件导航器中，选择ContentView.swift（内容查看）文件，可以浏览一下SwiftUI视图的组成结构。默认情况下，SwiftUI的视图文件包含两个结构体(Struct) 第一个结构体遵循View协议，描述视图的内容和布局。第二个结构体声明为第一个视图的预览视图。
						步骤5 在画布(Canvas)上，点击恢复(Resume)**按钮可以显示预览视图，也可以使用快捷键Command+Option+P
							
							
							注意：创建画布时可能会崩溃，我也不知道怎么回事
						步骤6 在body属性内部，修改文字Hello World为其它的不同的文字，当你在改变代码的同时，预览视图也会实时的更新对应的内容变化
							import SwiftUI\n\nstruct ContentView: View {\n    var body: some View {\n        Text("Hello, world!")\n    }\n}\n\nstruct ContentView_Previews: PreviewProvider {\n    static var previews: some View {\n        ContentView()\n    }\n}
							
				第二节 定制文本视图(Text View)
					简介：可能通过修改代码来改变一个视图的显示样式，也可以通过检查器获取视图可修改属性，然后再写对应的代码改变样式。在创建应用的过程中，可以同时使用源码编辑器、画布或者检查器，无论当前使用的是哪一个工具编辑视图，代码会保持和这些编辑器展示的样式一致
						
					使用检查器来定制视图的显示样式
						步骤1 在预览视图中，按下Command键的同时点击控件，会弹出一个编辑弹层，然后选择检查器(Inspect), 编辑弹层显示所有可以定制的视图属性，选中的控件不同，可以定制的属性集合也不相同
							
							在预览器中，按住 Command 键点击问候文本弹出编辑菜单，然后选择Inspect(Xcode 12中是Show SwiftUI Inspector)。\n虚拟机中就是Win键
						步骤2 使用检查器把文字更改为Turtle Rock（龟岩），也就是在应用中显示的第一个地标的名称\n\n
							
						步骤3 改变字体修改器为Title，使用系统字体修饰文字，可以自动按照用户在设备中设置的字体偏好大小进行调整。定制SwiftUI视图所调用的方法被称为视图修改器(Modifiers)，修改器在原视图的基础上修改部分显示样式和属性，返回一个新的视图，这样就可以让多个修改器串连进行，形成水平方向的链式调用，或者垂直方向的堆叠调用\n\n
						步骤4 手动在代码中添加foregroundColor(.green) 【前景颜色（.green）】属性修改器，就会把文字的颜色调整为绿色。代码是决定视图样式的根本，当我们使用检查器来改变或移除一个属性修改器时，Xcode也会在代码编辑器中同步改变或移除对应的修改器代码
							
						步骤5 在代码编辑器中，按下Command的同时点击Text单词也可以属性弹窗，从中选择检查器后，再点击Color弹出菜单，选择继承(Inherited)，让文字的颜色恢复成原来的黑色
							我的电脑中没有
							
				第三节 使用栈来组合视图
					目的：上一节创建了标题视图，接下来要添加一些文本视图来描述地标所在州及所在公园的名称等其它详细信息
						
					步骤
						步骤1 按下Command键的同时，点击Text视图的初始化代码打开结构化编辑弹窗，然后选择把控件嵌套在垂直栈中(Embed in VStack)，在栈中添加Text View控件可以从组件中直接拖进栈中完成\n\n
							
							注意：我是先将Text拖入代码的，才显示出了垂直栈这个选项
						第二步\n点击 Xcode 窗口右上角的(+)号按钮打开视图库，然后拖拽一个文本视图到代码中“Turtle Rock”文本视图后面。
						第三步\n使用“Joshua Tree National Park（约书亚树国家公园）”替换文本视图的占位文本。\n
							\nText("Turtle Rock")\n\n.font(.title)\n\nText("Joshua Tree National Park")\n\n}\n\n}
						第四步\n将位置文本的字体设置为subheadline（副标题）。\n\n
							.font(.title)\n\nText("Joshua Tree National Park")\n\n.font(.subheadline)\n\n}\n\n}
						第五步\n编辑 VStack 的初始化器将这些视图按头部边缘对齐。\n\n默认情况下，Stack 会根据视图的轴线居中对齐并根据上下文提供合适的间距。
							struct ContentView: View {\n    var body: some View {\n        VStack(alignment: .leading)\n//对齐：.leading\n{\n            Text("Turtle Rock")\n                .font(.title)
						第六步\n在画布中，按住 Command 键点击Joshua Tree National Park(约书亚树国家公园)，并选择Embed in HStack(嵌入到 HStack 中)。
							
						第七步\n在位置文本视图之后添加一个新的文本视图，将视图的占位文本改为公园所在的州，然后将它的字体改为subheadline。
						第八步\n为了让布局占满整个设备的宽度，通过在放置两个文本视图的 HStack 中添加一个Spacer空格【垫片】控件将位置视图和所在州视图分开。\n\nspacer控件会让它的容器视图使用父视图的全部空间，而不只是根据它的内容定义视图的大小。
							Text("Joshua Tree National Park")\n                    .font(.subheadline)\n                Spacer()//空格\n                Text("California")\n                    .font(.subheadline)
						第九步\n最后，使用padding()修饰器方法【填充（）】给地标的名字和详情一些额外的空间
							VStack(alignment: .leading) {\n            Text("Turtle Rock")\n                .font(.title)\n            HStack {\n                Text("Joshua Tree National Park")\n                    .font(.subheadline)\n                Spacer()\n                Text("California")\n                    .font(.subheadline)\n            }\n        }.padding()
				04 创建自定义的图像视图Image
					有了地标名称、地标位置及状态视图，下一步再添加一个地标图片视图。这个图片视图将自定义遮罩(mask)、边框(border)和阴影(shadow)
					我们从添加图片到项目的资源目录开始。
						第一步\n在项目文件的Resources文件夹中找到turtlerock.png文件，将它拖放到资源目录的编辑器中，Xcode 会为它创建一个新的图片集。
							
						第二步\n选择 File -> New -> File，打开模板选择器。在User Interface版块，选择SwiftUI View并点击Next，将文件命令为 CircleImage.swift 并点击Create。
						我们已经准备好要插入图片并修改显示以匹配设计的样式了。\n注意：接下来的操作都是在 CircleImage.swift中进行
						第三步\n使用带有 Turtle Rock 图片的Image(_:)初始化器替换原本的文本视图。
						第四步\n添加clipShape(Circle())【剪辑形状（圆形（）】调用对图片应用圆形剪切蒙版。\n\nCircle类型是一个可以用来当蒙版的形状类型，也可以作为视图画一个圆边或圆形
						第五步\n使用灰色的描边画出另外一个圆，然后作为叠层添加，为图像添加一个边框。
						第六步\n接下来，添加 10 个单位的阴影。
						第七步\n将边框的颜色换成白色。
							代码
								import SwiftUI\n\nstruct ContentView: View {\n    var body: some View {\n        VStack(alignment: .leading) {\n            Image("Turtle Rock")//龟岩\n                .clipShape(Circle())\n                .overlay(\n                    Circle().stroke(Color.white,lineWidth: 4))\n                .shadow(radius: 10)\n            HStack {\n                Text("Joshua Tree National Park")\n                    .font(.subheadline)\n                Spacer()\n                Text("California")\n                    .font(.subheadline)\n               \n            }\n        }\n        .padding()\n    }\n}\n\nstruct ContentView_Previews: PreviewProvider {\n    static var previews: some View {\n        ContentView()\n    }\n}\n
				05 将 UIKit 和 SwiftUI 视图一起使用
					概述：现在要创建一个地图视图，可以使用MapKit中的MKMapView视图类来渲染地图。要在SwiftUI中使用UIView及其子类，需要把这些UIView包裹在一个遵循UIViewRepresentable协议的SwiftUI视图中，SwiftUI中也包含适配WatchKit和AppKit的类似的协议。
					首先需要创建一个自定义视图用来容纳和显示MKMapView
						第一步\n选择 File -> New ->File，选择iOS作为平台，选择SwiftUI View模板，然后点击Next，将文件命名为MapView.swift并点击Create`。
						注意：接下来的操作全部都在MapView.swif中进行
						步骤2 代码中导入MapKit引用，声明MapView遵循UIViewRepresentable【有代表性的】协议。UIViewRepresentable协议要求实现两个方法UIView(context:)和updateUIView(_:context:)，第一个方法用来创建MKMapView，第二个方法用来配置视图响应状态变化
						步骤3 替换body，用makeUIView(context:)【制作 UI 视图（上下文 :)】方法来代替，创建并返回一个空的MKMapView
						步骤4 创建方法updateUIView(_:context:)【更新 UI 视图（_：上下文：）】，在方法内部设置地图视图的坐标为Turle Rock的中心。在静态模式下预览时，只会渲染swiftUI视图的部分，因为MKMapView是UIView的子类，所以需要切换到实时预览模式下才能看到地图被完全渲染出来
						步骤5 点击Live Preview(实时预览)按钮，可能需要点击Try Again和Resume按钮来激活预览模式的切换。切换到实时预览模式下不久就可以看到指定地标所在的地图位置了
						
							代码
								代码：\nimport SwiftUI\nimport MapKit\n\nstruct MapView: UIViewRepresentable//UI 视图可表示\n{    //func1:用来创建MKMapView\n    func makeUIView(context: Context) -> MKMapView {\n        MKMapView(frame: .zero)//在方法内部设置地图视图的坐标为Turle Rock的中心\n    }\n//func2:用来配置视图响应状态变化\n//    updateUIView=更新用户界面查看   context=上下文\n    func updateUIView(_ uiView: MKMapView, context: Context) {\n        let coordinate = CLLocationCoordinate2D(\n//           CL Location Coordinate 2D = CL 位置 坐标 2D\n            latitude: 34.011_286, longitude: -116.166_868)\n        //  latitude=纬度     longitude=经度\n        let span = MKCoordinateSpan(latitudeDelta: 2.0, longitudeDelta: 2.0)\n//        跨度=span   MKCoordinateSpan=MK 坐标跨度\n//        latitudeDelta=纬度德尔塔 ，longitudeDelta=经度德尔塔\n//        我推测德尔塔是区间取值的意思\n        let region = MKCoordinateRegion(center: coordinate, span: span)\n//        地区=region\n        uiView.setRegion(region, animated: true)//设置地区可视化\n        //animated: true=动画：真）\n    }\n}\n\nstruct MapView_Previews: PreviewProvider {\n    static var previews: some View {\n        MapView()\n    }\n}\n//在静态模式下预览时，只会渲染swiftUI视图的部分，因为MKMapView是UIView的子类，所以需要切换到实时预览模式下才能看到地图被完全渲染出来\n
				06 排版详情视图
					现在我们有了所有需要的视图-名字及位置、圆形图片和位置所在的地图。\n\n使用我们目前用过的工具，将自定义视图组合并创建最终的 landmark 详情视图设计
						
						代码
							代码：\n\nimport SwiftUI\n\nstruct ContentView: View {\n    var body: some View {\n        VStack {//body属性中嵌入一个VStack视图，它内部包含另一个VStack视图，内部的VStack视图又包含三个Text视图\n            MapView()//在外层VStack的顶部添加自定义的地图视图MapView，并使用frame(width:height:)设置视图大小。当只指定高度时，宽度会自动计算为父视图的宽度，在这里就是屏幕宽度\n                .edgesIgnoringSafeArea(.top)\n                //为了让地图的视图内容显示在状态栏的下方，可以给MapView添加edgesIgnoringSafeArea(.top)修改器，这可以让它在布局时忽略顶部的安全区域边距\n                .frame(height: 300)\n            CircleImage()//在MapView后面再添加一个CircleImage视图\n                .offset(y:-130)\n                .padding(.bottom,-130)\n            //为了让图片视图叠放在地图视图的上面，可以设置图片视图的垂直偏移量为-130，图片视图的底部内边距也为-130，这个效果就是把图片垂直上移了130，同时和下面的文字区域留出了130的空白分隔区\n            VStack(alignment: .leading) {\n                Text("Turtle Rock")\n                    .font(.title)\n                HStack {\n                    Text("Joshua Tree National Park")\n                        .font(.subheadline)\n                    Spacer()\n                    Text("California")\n                        .font(.subheadline)\n                   \n                }\n            }\n            .padding()\n            //间隔= Spacer\n            Spacer()//在外层VStack内部的最下面加上Spacer，可以让上面的视图内容顶到屏幕的上边\n        }\n       \n       \n    }\n}\n\nstruct ContentView_Previews: PreviewProvider {\n    static var previews: some View {\n        ContentView()\n    }\n}\n
							
					步骤
						在项目工程浏览器中选择ContentView.swift【内容视图】文件
						body属性中嵌入一个VStack视图，它内部包含另一个VStack视图，内部的VStack视图又包含三个Text视图
						在外层VStack的顶部添加自定义的地图视图MapView，并使用frame(width:height:)设置视图大小。当只指定高度时，宽度会自动计算为父视图的宽度，在这里就是屏幕宽度
						点击Live Preview按钮进入实时预览模式，查看地图渲染情况。在实时预览模式下可以编辑视图，最新的改动也可以实时的刷新出来。
						在MapView后面再添加一个CircleImage视图
						为了让图片视图叠放在地图视图的上面，可以设置图片视图的垂直偏移量为-130，图片视图的底部内边距也为-130，这个效果就是把图片垂直上移了130，同时和下面的文字区域留出了130的空白分隔区
						在外层VStack内部的最下面加上Spacer，可以让上面的视图内容顶到屏幕的上边
						为了让地图的视图内容显示在状态栏的下方，可以给MapView添加edgesIgnoringSafeArea(.top)【 边缘忽略安全区域（.top）】修改器 ，这可以让它在布局时忽略顶部的安全区域边距
			二 创建列表和导航
				目的：\n地标详情页视图已经创建完成，我们需要提供一种方式让用户可以查看完整的地标列表，并且可以查看每一个地标的详情\n\n下面会创建一个可以展示任何地标信息的视图，并动态生成一个可滚动列表，用户可以点击列表项去查看地标的详细信息。优化视图显示时，可以使用Xcode画布来渲染多个不同设备大小下的预览视图。
					检查是否理解
						
							补充
								forEach() 方法用于调用数组的每个元素，并将元素传递给回调函数。
								\.self作为id的键索引
									下面我们详细说下id。\nid & Hashable\npublic init(_ data: Data, id: KeyPath<Data.Element, ID>, @ViewBuilder content: @escaping (Data.Element) -> Content)\n\nid 要求我们传入的是一个 KeyPath，且ID必须实现Hashable。而我们常见的数据类型 Int/String/...都默认实现Hashable。\n通过指定 id 的初始化方式适用于元素没有实现 Identifiable 的场景。\n\n链接：https://juejin.cn/post/6984753286058344456\n
						
						
						
				第一节 了解样本数据
					在第一个教程中，我们是将信息硬编码到视图中。这里我们学习如何将数据传入自定义视图显示。\n\n通过下载启动项目开始并熟悉示例数据。
						
							
					步骤：
						步骤2 在项目导航器中选择Resources->landmarkData.json，在后面的教程中我们都会使用这个样本数据文件\n存储和表示数据：{JSON（JavaScript Object Notation, JS对象简谱）是一种轻量级的数据交换格式。它基于 ECMAScript（European Computer Manufacturers Association, 欧洲计算机协会制定的js规范）的一个子集，采用完全独立于编程语言的文本格式来存储和表示数据。简洁和清晰的层次结构使得 JSON 成为理想的数据交换语言。 易于人阅读和编写，同时也易于机器解析和生成，并有效地提升网络传输效率。}
							
						步骤3 注意，之前的ContentView视图，已经被改名为LandmarkDetail（地标详情）了，在本教程和后面的教程中，还会创建一些其它的视图
							
							第一步\n在项目导航器中，选择Models -> Landmark.swift。\n\nLandmark.swift声明了Landmark结构体，它存储了所有的App需要展示的地标信息，并从landmarkData.json中导入一个地标数据的数组。
								
				第二节 创建行视图
					目的：\n本教程中创建的第一个视图就是用来显示每个地标的行视图，行视图把地标的相关信息存储在一个属性中，一行就可以代表一个地标，稍后就会把这些行组合成为一个列表。
						
						代码
							\nimport SwiftUI\n\nstruct LandmarkRow: View {\n    var landmark: Landmark\n    // 添加landmark属性做为LandmarkRow视图的一个存储属性。当添加landmark属性后，预览视图可能会停止工作，因为LandmarkRow视图初始化时需要有一个landmark实例。要想修复预览视图，需要修改Preview Provider\n    \n    var body: some View {\n        HStack {\n//            将当前的文本视图嵌套到HStack中\n            landmark.image\n//                在文本视图前面添加一个图片，后面添加一个Spacer控件完成行视图\n                .resizable() //可调整大小\n                .frame(width: 50, height: 50)\n            \n            Text(landmark.name)\n            //用landmark属性的name字段修改文本视图。\n            \n            Spacer()\n//            间隔\n        }\n    }\n}\n\nstruct LandmarkRow_Previews: PreviewProvider {\n    static var previews: some View {\n        LandmarkRow(landmark: landmarkData[0])\n    }\n}
							
					步骤
						步骤1 创建一个名为LandmarkRow.swift的SwiftUI视图
							landmark row create
								
						步骤2 如果预览视图没有出现，可以选择菜单编辑器->画布，打开画布，并点击Resume进行预览，或者使用Command+Option+Enter快捷键调出画面，再使用Command+Option+P快捷键开始预览模式
						步骤3 添加landmark属性做为LandmarkRow视图的一个存储属性。当添加landmark属性后，预览视图可能会停止工作，因为LandmarkRow视图初始化时需要有一个landmark实例。要想修复预览视图，需要修改Preview Provider
						步骤4 在LandmarkRow_Previews的静态属性previews中给LandmarkRow初始化器中传入landmark参数，这个参数使用landmarkData数组的第一个元素。预览视图当前显示Hello, World
						步骤5 在一个HStack中嵌入一个Text
						步骤6 修改这个Text，让它使用landmark属性的name字段
						步骤7 在Text视图前面添加一个图片视图，在Text视图后面添加Spacer视图
				03 定制行视图预览
					Xcode的画布会在当前编辑器自动识别并显示任意遵从PreviewProvider协议的类型。一个预览提供器会返回一个或多个视图，还有配置尺寸和设备的选项。\n\n我们可以在预览提供器中定制返回的内容，这样可以渲染对我们最有帮助的预览图
						
						代码
							\nimport SwiftUI\n\nstruct LandmarkRow: View {\n    var landmark: Landmark\n    // 添加landmark属性做为LandmarkRow视图的一个存储属性。当添加landmark属性后，预览视图可能会停止工作，因为LandmarkRow视图初始化时需要有一个landmark实例。要想修复预览视图，需要修改Preview Provider\n    \n    var body: some View {\n        HStack {\n//            将当前的文本视图嵌套到HStack中\n            landmark.image\n//                在文本视图前面添加一个图片，后面添加一个Spacer控件完成行视图\n                .resizable() //可调整大小\n                .frame(width: 50, height: 50)\n            \n            Text(landmark.name)\n            //用landmark属性的name字段修改文本视图。\n            \n            Spacer()\n//            间隔\n        }\n    }\n}\n\nstruct LandmarkRow_Previews: PreviewProvider {\n    static var previews: some View {\n        Group {\n//将返回的行视图嵌套在Group中，并将第一行重新加回来。\n            \n//            Group是一个组合视图的容器。Xcode在画布中会将组的子视图渲染为单独的预览。\n            LandmarkRow(landmark: landmarkData[0])\n            LandmarkRow(landmark: landmarkData[1])\n\n        }\n//        为了简化代码，我们将previewLayout(_:)调用移动到group声明的外面。\n        .previewLayout(.fixed(width: 300, height: 70))\n//        使用previewLayout(_:)修饰器设置行在列表中的预估尺寸。\n    }\n}\n
					步骤
						步骤1 在LandmarkRow_Previews中，把landmark参数更新为landmarkData数组的第二个元素，预览视图会立即刷新反映第二个元素的渲染情况
						步骤2 使用previewLayout(_:)【预览布局(_:)】修改器设置一个行视图在列表中显示的尺寸大小。可以使用Group的方式，返回多个不同场景下的预览视图
						步骤3 把预览的行视图包裹在Group中，把之前的第一个行视图也加进去。Group是一个容器，它可以把视图内容组织起来，Xcode会把Group内的每个子视图当作画布内一个单独的预览视图处理
						步骤4 为了简化代码，可以把previewLayout(_:)【预览布局(_:)】这个修改器应用到外层的Group上，Group的每一个子视图会继承自己所处环境的配置。对preivew provider的修改只会影响预览画布的表现，对实际的应用不会产生影响。
							preview group coniguration
				第四节 创建地标列表
					使用SwiftUI列表类型可以展示平台相关的列表视图。列表的元素可以是静态的，类似于栈内部的子视图，也可以是动态生成的视图，也可以混合动态和静态的视图。
						代码
							\nimport SwiftUI\n\nstruct landmarkList: View {\n    var body: some View {\n        List{\n            LandmarkRow(landmark: landmarkData[0])\n            LandmarkRow(landmark: landmarkData[1])\n//            landmarkData数组头两个元素创建两个LandmarkRow实例作为子视图。\n        }\n    }\n}\n//预览会显示两个地标显示在iOS样式的列表中\nstruct landmarkList_Previews: PreviewProvider {\n    static var previews: some View {\n        landmarkList()\n    }\n}\n
					步骤
						步骤1 创建SwiftUI视图，命名为LandmarkList.swift
						步骤2 用List替换默认创建的Text，并将前两个LandmarkRow【地标行】实例做为列表的子元素，预览视图中会以列表的形式展示出两个地标
							
				05 让列表动态生成\n
					相对于亲自指定列表的元素，我们可以直接从集合中生成行元素。\n\n我们可以通过传入集合的数据并使用闭包为集合中的每一个元素提供一个视图来创建一个列表显示集合中的元素。这个列表通过提供的闭包将集合中的每个元素转换成一个子视图。\n闭包：\n闭包(Closures)是自包含的功能代码块，可以在代码中使用或者用来作为参数传值。\nSwift 中的闭包与 C 和 Objective-C 中的代码块（blocks）以及其他一些编程语言中的 匿名函数比较相似。\n全局函数和嵌套函数其实就是特殊的闭包。
						
						代码
							\nimport SwiftUI\n\nstruct landmarkList: View {\n    var body: some View {\n        List(landmarkData/*,id: \.id*/)//唯一标识符**keypath:**\.id\n//移除keypath\.id，因为landmarkData数据集合的元素已经遵循了Identifiable协议，所以在列表初始化器中可以直接使用，不需要手动标明数据的唯一标识符了\n        {\n            Landmark in\n            LandmarkRow(landmark: Landmark)\n        }\n    }\n}\n//预览会显示两个地标显示在iOS样式的列表中\nstruct landmarkList_Previews: PreviewProvider {\n    static var previews: some View {\n        landmarkList()\n    }\n}\n
					步骤
						步骤1 从列表中移除两个静态指定的行视图，给列表初始化器传入landmarkData数据，列表要配合可辨别的数据类型使用。想让数据变成可辨别的数据类型有两种方法:
							传入一个keypath指定数据中哪一个字段用来唯一标识这个数据元素。
							让数据遵循Identifiable协议
						步骤2 在闭包中返回一个LandmarkRow视图，List初始化器中指定数据集合landmarkData和唯一标识符**keypath:**\.id，这样列表就会动态生成，如下图所示
						keypath identifier list data
							
						步骤3 切换到文件Landmark.swfit，声明Landmark类型遵循Identifiable协议，因为Landmark类型已经定义了id属性，正好满足Identifiable协议，所以不需要添加其它代码
						identifiable data
						步骤4 现在切换回文件LandmarkList.swift，移除keypath\.id，因为landmarkData数据集合的元素已经遵循了Identifiable协议，所以在列表初始化器中可以直接使用，不需要手动标明数据的唯一标识符了
						identifiable list
				第六节 设置从列表页到详情页的页面导航\n对接
					概述：\n地标列表可以正常渲染展示，但是列表的元素点击后没有反应，跳转不到地标详情页。现在就要给列表添加导航能力，把列表视图嵌套到NavigationView视图中，然后把列表的每一个行视图嵌套进NavigationLink视图中，就可以建立起从地标列表视图到地标详情页的跳转。
						
					步骤
						步骤1 把动态生成的列表视图嵌套进一个NavigationView视图中
							
						步骤2 调用navigationBarTitle(_:)修改器设置地标列表显示时的导航条标题
							landmark list navigation view
						步骤3 在列表的闭包中，将每一个行元素包裹在NavigationLink中返回，并指定LandmarkDetail视图为目标视图
							navigation link
						步骤4 切换到实时预览模式下可以直接点击地标列表的任意一行，现在就可以跳转到地标详情页了。
							list navigation
					
					代码
						\nimport SwiftUI\n\nstruct landmarkList: View {\n    var body: some View {\n        NavigationView{\n//             把动态生成的列表视图嵌套进一个NavigationView视图中\n        List(landmarkData/*,id: \.id*/)//唯一标识符**keypath:**\.id\n//移除keypath\.id，因为landmarkData数据集合的元素已经遵循了Identifiable协议，所以在列表初始化器中可以直接使用，不需要手动标明数据的唯一标识符了\n        \n        \n        {\n            Landmark in\n            NavigationLink (destination: LandmarkDetail())\n//            在列表的闭包中，将每一个行元素包裹在NavigationLink中返回，并指定LandmarkDetail视图为目标视图\n            {\n                LandmarkRow(landmark: Landmark)\n                \n            }\n        }\n            .navigationBarTitle(Text("landmarks"))\n//            调用navigationBarTitle(_:)修改器设置地标列表显示时的导航条标题\n        }\n    }\n}\n//预览会显示两个地标显示在iOS样式的列表中\nstruct landmarkList_Previews: PreviewProvider {\n    static var previews: some View {\n        landmarkList()\n    }\n}\n
				第七节 子视图传入数据
					LandmarkDetail（地标细节）视图目前还是使用写死的数据进行展示，与LandmarkRow视图一样，LandmarkDetail视图及它内部的子视图也需要传入landmark数据，并使用它来进行实际的展示\n\n从LandmarkDetail的子视图(CircleImage、MapView)开始，需要把它们都改造成为使用传入的数据进行展示，而不是在布局代码中写死数据展示
						
					步骤
						第一步\n在CircleImage.swift文件中，添加一个存储图片的属性到CircleImage类中。\n\nstruct CircleImage: View {\n    var image: Image\n\n    var body: some View {\n        image
							第二步\n更新预览提供器，传入Turtle Rock的图片。\n\nstruct CircleImage_Previews: PreviewProvider {\n    static var previews: some View {\n        CircleImage(image: Image("turtlerock"))\n    }\n}
								
						第三步\n在MapView.swift文件中，为MapView类添加一个坐标属性，并使用这个属性取代硬编码的经度和纬度。\n\nstruct MapView: UIViewRepresentable {\n    var coordinate: CLLocationCoordinate2D\n\n    func makeUIView(context: Context) -> MKMapView {\n        MKMapView(frame: .zero)
							第四步\n更新预览提供器并传入数据数组中的第一个地标的坐标。\n\nstruct MapView_Previews: PreviewProvider {\n    static var previews: some View {\n        MapView(coordinate: landmarkData[0].locationCoordinate)\n    }\n}
								
						第五步\n在LandmarkDetail.swift文件中，为LandmarkDetail类添加一个Landmark属性。\n\nstruct LandmarkDetail: View {\n    var landmark: Landmark\n\n    var body: some View {\n        VStack {
							第六步\n更新预览提供器，使用landmarkData数组的第一个地标。\n\nstruct LandmarkDetail_Previews: PreviewProvider {\n    static var previews: some View {\n        LandmarkDetail(landmark: landmarkData[0])\n    }\n}
								
						第七步\n将需要的数据传入那些自定义的类型中。\n\n    var body: some View {\n        VStack {\n            MapView(coordinate: landmark.locationCoordinate)\n                .edgesIgnoringSafeArea(.top)\n                .frame(height: 300)\n\n            CircleImage(image: landmark.image)\n                .offset(x: 0, y: -130)\n                .padding(.bottom, -130)\n\n            VStack(alignment: .leading) {\n                Text(landmark.name)\n                    .font(.title)\n                HStack(alignment: .top) {\n                    Text(landmark.park)\n                        .font(.subheadline)\n                    Spacer()\n                    Text(landmark.state)\n                        .font(.subheadline)\n                }\n            }
							第八步\n最后，在调用navigationBarTitle(_:displayMode:)修饰器在展示详情页的时候添加导航栏标题。\n\n            Spacer()\n        }\n        .navigationBarTitle(Text(landmark.name), displayMode: .inline)\n    }\n}
						第九步\n在SceneDelegate.swift{场景委托}文件中，将App顶层的视图换成LandmarkList。\n\n当App在模拟器中而不是预览器中运行的时候会从定义的SceneDelegate中的顶层视图开始。\n\n        if let windowScene = scene as? UIWindowScene {\n            let window = UIWindow(windowScene: windowScene)\n            window.rootViewController = UIHostingController(rootView: LandmarkList())\n            self.window = window\n            window.makeKeyAndVisible()
						第十步\n在LandmarkList.swift文件中，将当前地标传入LandmarkDetail目标。\n\n        NavigationView {\n            List(landmarkData) { landmark in\n                NavigationLink(destination: LandmarkDetail(landmark: landmark)) {\n                    LandmarkRow(landmark: landmark)\n                }
				08 动态生成预览
					接下来，我们会在LandmarkList_Previews预览提供器中添加代码在不同的设备中渲染列表视图。默认情况下，预览器会渲染当前选择的scheme（方案）的设备，可以通过调用previewDevice(_:)（预览设备）修饰器方法改变预览的设备。
						
					步骤
						步骤1 改变当前预览列表，让它渲染在iPhone SE设备上。可以使用Xcode Scheme菜单上的设备名称来指定渲染设备。
							
						步骤2 在列表的预览视图中，还可以把LandmarkList嵌套进入ForEach实例中，使用设备数组名作为数据。ForEach运算作用在集合类型的数据上，就和列表使用集合类型数据一样，可以在子视图使用的任何场景下使用ForEach，例如：stack、list、group等。当元素数据是简单值类型时(例如字符串类型)，可以使用\.self作为keypath去标识
							
						步骤3 使用previewDisplayName(_:)修改器可以给预览视图添加设备标签
						步骤4 可以在画布上多设置几个设备进行预览，比较不同设备下视图的展示情况
							
					补充
						forEach() 方法用于调用数组的每个元素，并将元素传递给回调函数。
							\.self作为id的键索引
								下面我们详细说下id。\nid & Hashable\npublic init(_ data: Data, id: KeyPath<Data.Element, ID>, @ViewBuilder content: @escaping (Data.Element) -> Content)\n\nid 要求我们传入的是一个 KeyPath，且ID必须实现Hashable。而我们常见的数据类型 Int/String/...都默认实现Hashable。\n通过指定 id 的初始化方式适用于元素没有实现 Identifiable 的场景。\n\n链接：https://juejin.cn/post/6984753286058344456\n
					
			三 处理用户输入
				目的：\n在Landmark应用中，标记喜爱的地方，过滤地标列表，只显示喜欢的地标。要增加这些特性，首先要在列表上添加一个开关，用来过滤用户喜欢的地标。在地标上添加一个星标按钮，用户可以点击它来标记这个地标为自己喜欢的。
					检查是否理解
						
						
				第一节 标记用户最喜欢的地标
					
					步骤
						步骤1 打开工程项目，在项目导航下选择LandmarkRow.swift文件
						步骤2 在空白占位后面添加一个if表达式，if表达式判断是否当前地标是用户喜欢的，如果用户标记当前地标为喜欢就显示星标。可以在SwitUI的代码块中使用if语句来条件包含视图
						步骤3 由于系统图片是矢量类型的，可以使用foregroundColor(_:)【前景色（_：）】来改变它的颜色。当地标landmark的isFavorite属性为真时，星标显示，稍后会讲怎么修改属性值。
						
						代码
							/*\nSee LICENSE folder for this sample’s licensing information.\n\nAbstract:\nA single row to be displayed in a list of landmarks.\n*/\n\nimport SwiftUI\n\nstruct LandmarkRow: View {\n    var landmark: Landmark\n\n    var body: some View {\n        HStack {\n            landmark.image\n                .resizable()\n                .frame(width: 50, height: 50)\n            Text(landmark.name)\n            Spacer()\n//            在Spacer控件后，添加一个if语句判断当前地标是否是收藏的，并在语句中添加星形图片\n            if landmark.isFavorite{\n                Image(systemName: "star.fill")\n                    .imageScale(.medium)\n                    .foregroundColor(.yellow)\n//                由于系统图片是矢量的，我们可以使用foregroundColor(_:)修饰器改变它们的颜色。\n                \n//                星形控件会在地标的isFavorite属性为true时显示。我们之后会学习如何修改这个属性。\n            }\n        }\n    }\n}\n\nstruct LandmarkRow_Previews: PreviewProvider {\n    static var previews: some View {\n        Group {\n            LandmarkRow(landmark: landmarkData[0])\n            LandmarkRow(landmark: landmarkData[1])\n        }\n        .previewLayout(.fixed(width: 300, height: 70))\n    }\n}\n
				第二节 过滤列表
					可以定制地标列表，让它只显示用户喜欢的地标，或者显示所有的地标。要实现这个功能，需要给LandmarkList视图类型添加一些状态变量\n\n\n状态(State)是一个值或者一个值的集合，会随着时间而改变，同时会影响视图的内容、行为或布局。在属性前面加上@State修饰词就是给视图添加了一个状态值
						
					步骤
						步骤1 选择LandmarkList.swift文件，并给LandmarkList添加一个名为showFavoritesOnly的状态，初始值设置为false
						步骤2 点击Resume按钮或快捷键Command+Option+P刷新画布。当对视图进行添加或修改属性等结构性改变时，需要手动刷新画布
						步骤3 代码中通过检查showFavoritesOnly属性和每一个地标的isFavorite属性值来过滤地标列表所展示的内容
						
						代码
							/*\nSee LICENSE folder for this sample’s licensing information.\n\nAbstract:\nA view showing a list of landmarks.\n*/\n\nimport SwiftUI\n\nstruct LandmarkList: View {\n    \n    @State var showFavoritesOnly = false\n//    给LandmarkList添加一个名为showFavoritesOnly的状态，初始值设置为false\n    \n    var body: some View {\n        NavigationView {\n            List(landmarkData) { landmark in\n                \n                if self.showFavoritesOnly||landmark.isFavorite{\n//                    代码中通过检查showFavoritesOnly属性和每一个地标的isFavorite属性值来过滤地标列表所展示的内容\n                NavigationLink(destination: LandmarkDetail(landmark: landmark)) {\n                    LandmarkRow(landmark: landmark)\n                }\n            }\n            }\n            .navigationBarTitle(Text("Landmarks"))\n        }\n    }\n}\n\nstruct LandmarkList_Previews: PreviewProvider {\n    static var previews: some View {\n        ForEach(["iPhone SE", "iPhone XS Max"], id: \.self) { deviceName in\n            LandmarkList()\n                .previewDevice(PreviewDevice(rawValue: deviceName))\n                .previewDisplayName(deviceName)\n        }\n    }\n}\n
				第三节 添加控件来切换状态
					为了让用户控制地标列表的过滤器，需要添加一个可以修改showFavoritesOnly值的控件，传递一个绑定关系给toggle（切换）控件可以实现
					一个绑定关系(binding)是对可变状态的引用。当用户点击toggle控件，从开到关或从关到开，toggle控件会通过绑定关系对应的更新视图的状态
						
					步骤
						步骤1 创建一个嵌套的ForEach组来把地标数据转换成地标行视图。在一个列表中组合静态和动态视图，或者组合两个甚至多个不同的动态视图组，使用ForEach类型动态生成而不是给列表传入数据集合生成列表视图
						步骤2 添加一个Toggle视图作为列表的每一个子视图，传入一个showFavoritesOnly的绑定关系。使用$前缀来获得一个状态变量或属性的绑定关系
						步骤3 实时预览模式下，点击Toggle控件来验证过滤器的功能
						
						
				04 为存储使用可观察对象
					为了准备让用户控制哪个地标是收藏了的，我们首先需要将地标数据存储在可观察对象中。\n\n可观察对象是一个为数据自定义的对象，在SwiftUI环境中可以将存储与视图绑定。SwiftUI会监视可观察对象可能会导致UI变化的数据改变，并在数据改变后显示正确的视图版本。
						
					步骤
						步骤1 创建一个名为UserData.swift的文件
						步骤2 声明一个遵循ObservableObject协议的新数据模型，ObservableObject协议来自响应式框架Combine。SwiftUI可以订阅可观察对象，并在数据发生改变时更新视图的显示内容
						步骤3 添加存储属性showFavoritesOnly和landmarks，并赋予初始值。可观察对象需要对外公布内部数据的任何改动，因此订阅此可观察对象的订阅者就可以获得对应的数据改动信息
						步骤4 给新建的数据模型的每一个属性添加@Published属性修饰词
					代码
						\nimport SwiftUI\n//SwiftUI可以订阅可观察对象，并在数据改变的时候更新需要刷新的视图\nimport Combine//声明一个新的model遵从Combine(合)框架中的Observable （可观察 对象）Object协议。\n\nfinal class UserData: ObservableObject  {\n    @Published var showFavoritesOnly = false\n    @Published var landmarks = landmarkData\n    //为showFavoritesOnly和地标数组添加存储属性，并初始化。\n    \n    \n}\n
				05 在视图中使用model模型对象
					现在我们已经创建了UserData对象，需要更新视图将其作为数据存储
						
					步骤
						步骤1 在LandmarkList.swift文件中，使用@EnvironmentObject{环境对象}修饰的userData属性来替换原来的showFavoritesOnly状态属性，并对预览视图调用environmentObject(_:)修改器。只要environmentObject(_:)修改器应用在视图的父视图上，userData就能够自动获取它的值。
						步骤2 替换原来使用showFavoritesOnly状态属性的地方，改为使用userData中的对应属性。与@State修饰的属性一样，也可以使用$前缀访问userData对象的成员绑定引用
						步骤3 创建ForEach实例时使用userData.landmarks做为数据源
						envrionment object
							
						步骤4 在SceneDelegate.swift中，对LandmarkList视图调用environmentObject修改器，这样可以把UserData的数据对象绑定到LandmarkList视图的环境变量中，子视图可以获得父视图环境中的变量。此时如果在模拟器或者真机上运行应用，也可以正常展示视图内容
						scene delegate
							
						步骤5 更新LandmarkDetail视图，让它从父视图的环境变量中取要展示的数据。之后在更新地标的用户喜爱状态时，会用到landmarkIndex这个变量
						landmark detail environment
							
						步骤6 切换到LandmarkList.swift文件，并打开实时预览视图去验证所添加的功能是否正常工作
						landmark list environment
				第六节 为每一个地标创建一个喜爱按钮
					Landmark这个应用可以在喜欢和不喜欢的地标列表间进行切换了，但喜欢的地标列表还是硬编码形成的，为了让用户可以自己标记哪个地标是自己喜欢的，需要在地标详情页添加一个标记喜欢的按钮
						
					步骤
						步骤1 在LandmarkDetail.swift的HStack中添加地标名称的Text
						步骤2 在地标名称的Text控件旁边添加一个新的按钮控件。使用if-else条件语句设置不同的图片显示状态表示这个地标是否被用户标记为喜欢。在Button的动作闭包中，使用了landmarkIndex去修改userData中对应地标的数据。
						favorite star button
							
						步骤3 切换到landmarkList.swift，并开启实时预览模式。当从列表页导航进入详情页后，点击喜欢按钮，喜欢的状态会在返回列表页后与列表中对应的地标喜欢状态保持一致，因为列表页和详情页的地标数据使用的是同一份，所以可以在不同页面间保持状态同步。
		2 绘制和动画
			四 绘制路径和形状\n(主要是3d方面，非编程重点，注重3d绘图
				第一节 创建徽章视图
					
					步骤
						步骤1 选择文件->新建->文件，然后从iOS文件模板列表中选择SwiftUI View。点击下一步(Next)，输入文件名Badge后点击创建(Create)
						create file
						name file
						步骤2 调整Badge视图，暂时先让它显示"Badge"文本，一会儿再绘制徽章的形状
						badge text
				第二节 绘制徽章背景
					
					步骤
						步骤1 查看在文件HexagonParameters.swift（六边形参数.swift）中的代码。HexagonParameters结构体定义了绘制徽章六边形形状的控制点参数。不需要修改这些绘制相关的数据，仅仅使用这些数据指定绘制徽章形状时，线段和曲线的控制点位置。
						hexagonal data
						步骤2 在Badge.swift文件中，绘制徽章的形状并使用fill修改器给六边形填充颜色，形成一个视图。使用路径可以把多条直线、曲线或其它绘制形状的基本笔划连成一个复杂的图形，就像形成徽章六边形背景这样.
						Path
						步骤3 给路径添加起点，move(to:)方法可以把绘图光标移动到绘图中的一点，准备绘制的起点
						path start point
						步骤4 使用六边形的绘制参数数据HexagonParameters，依次绘制六边形的边，形成大致轮廓.addLine(to:)方法会使用当前绘图光标所在点为起点，方法参数中指定的点为终点绘制直线。目前六边形看起来有点问题，不过不要担心，这是意料中的事，下面的步骤做完，六边形的形状就会和开头显示的徽章的六边形形状一致了
						path fill
						步骤5 使用addQuadCurve(to:control:)方法绘制贝塞尔曲线，让六边形的角变的更圆润些。
						badge hexagonal
						步骤6 把徽章路径包裹在一个Geometry Reader中，这样徽章可以使用容器的大小，定义自己绘制的尺寸，这样就不需要硬编码绘制尺寸了(100)。当绘制区域不是正方形时，使用绘制区域的最小边长(长宽中哪个最小使用哪个)作为绘制徽章背景的边长，并保持徽章背景的长宽比为1:1
						geometry reader
						步骤7 使用xScale和xOffset参数调整变量，把徽章几何绘图区域居中绘制出来
						badge square
						步骤8 把黑色实心填充色改为渐变色，使徽章看上去和开始设计的样式一致
						badge gradient
						步骤9 渐变色上再使用aspectRatio(_:contentMode:)修改器，让渐变色按内容宽高比进行成比例渐变填充。保持1:1的长宽比，徽章背景可以保持居中在徽章视图中，不管徽章视图本身是不是正方形
						badge center
				第三节 绘制徽章符号
					地标徽章中心有一个以地标App图标中的山峰图形改造形成的标志。山峰这个符号由两个形状组成，一个是表示山顶被雪覆盖的部分，另一个是山体。这里会使用有一定间距的两个局部三角形形状绘制这个徽章符号
						
					步骤
						步骤1 把之前的徽章视图形状抽出来单独形成一个BadgeBackground视图，并生成一个新的视图文件BadgeBackground.swift
						badge background
						refactor badge
						步骤3 创建名为BadgeSymbol的自定义视图，这个视图是一个山峰的形状，把这个形状复制多次并按一定角度旋转多次拼成一个徽章的图案
						badge symbol
						步骤4 使用pathAPI来绘制徽章符号的上半部分，试着调节spacing、topWidth、topHeight的系数，观察这些系数是怎么影响图形绘制的结果的
						badge symbol top
						步骤5 绘制徽章图案的下半部分，使用move(to:)把绘图光标移到另一个图形绘制的起点，绘制新的形状
						badge symbol bottom
						步骤6 用紫色填充徽章符号
						badge symbol fill
				第四节 组合徽章的前景符号和背景形状
					概述：\n徽章的设计需要让山峰形状在背景之上进行多次旋转。\n\n我们先定义一个新的类型用于旋转，并利用ForEach对山峰形状使用相同的调整生成多个拷贝。
						
					步骤
						步骤1 创建RotatedBadgeSymbol视图封装旋转徽章符号，调整旋转的角度，并在预览视图中查看效果
							
							\nimport SwiftUI\n//旋转徽章符号\nstruct RotatedBadgeSymbol: View {\n    \n    let angle: Angle//角度\n    \n    \n    var body: some View {\n        BadgeSymbol()\n            .padding(-60)//填充\n            .rotationEffect(angle, anchor: .bottom)\n//        旋转效应 ,锚点：.底部\n    }\n}\n\nstruct RotatedBadgeSymbol_Previews: PreviewProvider {\n    static var previews: some View {\n        RotatedBadgeSymbol(angle: Angle(degrees: 5))\n//        角度（度：5））\n    }\n}\n
						步骤2 在Badge.swift中，使用ZStack把徽章图标放在徽章背景层上面。此时会发现，徽章符号的尺寸相比徽章背景大了许多，这不符合最初设计的预期
							
							//\nimport SwiftUI\n\nstruct Badge: View {\n    \n    var badgeSymbols: some View {\n        RotatedBadgeSymbol(angle: Angle(degrees: 0)).opacity(0.5)\n        //角度（度：0））。 不透明度（0.5）\n    }\n    \n    \n    var body: some View {\n        ZStack {//Z轴\n            BadgeBackground()\n            self.badgeSymbols\n//            徽章背景（）\n//            自己 。 徽章符号\n        }\n//        将BadgeBackground放回Badge的body属性中恢复徽章背景\n    }\n}\n\nstruct Badge_Previews: PreviewProvider {\n    static var previews: some View {\n        Badge()\n    }\n}
						步骤3 通过读取包围它的geometry（几何学）和 缩放修正 徽章符号的尺寸。
						步骤4 使用ForEach复制多个徽章图标，按360度周解均分，每一个徽章符号都比前一个多旋转45度，这种就会形成一个类似太阳和徽章图标
					检查是否理解
						几何阅读器:问题1 GeometryReader的作用是什么
							
						
							
						
							
			五  视图动画和转场
				概述\n在使用SwiftUI的时候，无论效果在哪里，我们都可以单独的让视图的变化动起来，或者让视图的状态的变化动态化。SwiftUI会为我们处理那些组合的、层叠的以及可中断的动画的复杂性。\n在这个教程中，我们会动画化用户在使用Landmarks App远足时的轨迹视图。通过使用animation(_:（）)动画修饰器，我们可以了解为视图添加动画是多么简单的事。
					检查是否理解
						
							
						
						
				第一节 给每个视图单独添加动画
					在视图上使用animation(_:)修改器时，SwiftUI会在视图的任何可进行动画的属性发生改变时产生对应的动画效果。视图的颜色、不透明度、旋转角度、大小及一些其它属性都是可进行动画的\n\n
						
					步骤
						步骤1 在HikeView.swift【远足视图】中，打开实时预览，体验一下图表的打开和隐藏，此时的状态改变时是没有添加动画效果的。在本篇的实践中，保持实时预览一直打开，每一步修改的效果就可以实时的看到
							live preview animation
								
						步骤2 给显示/隐藏切换的箭头按钮添加旋转动画，会发现现在按钮点击时的旋转有一个动画过渡的效果了
							rotate button animation video
								
						步骤3 当视图从隐藏到展示时，让切换按钮变大1.5倍
							rotate button scale
								
						步骤4 把动画的类型从easeInOut【轻松进出】改为spring()【弹簧】。SwiftUI包含一些预设或可自定义的动画类型，像弹簧(spring)动画和类型液体(fluid)动画类型。可以调整动画开始前的等待时长、动画的速度也可以指定让动画循环重复的进行
							rotate button spring
								
						步骤5 如果只想让按钮具有缩放动画而不进行旋转动画，可以在scaleEffect【规模效应】添加animation(nil)【动画（无）】来实现。可以在这里做一些实验，如果把其它的一些动画效果结合在一起，会怎么样
							rotate button no rotate\n【旋转按钮不旋转】
								
						步骤6 学下一节之前，把本节中添加的animation(_:)修改器都去掉
							rotate button resume\n【旋转按钮恢复】
								
					代码
						\nimport SwiftUI\n\nstruct HikeView: View {\n    var hike: Hike\n    @State private var showDetail = false\n    \n    var body: some View {\n        VStack {\n            HStack {\n                HikeGraph(hike: hike, path: \.elevation)\n                    .frame(width: 50, height: 30)\n                    .animation(nil)\n                \n                VStack(alignment: .leading) {\n                    Text(hike.name)\n                        .font(.headline)\n                    Text(hike.distanceText)\n                }\n                \n                Spacer()\n\n                Button(action: {\n                    self.showDetail.toggle()\n                }) {\n                    Image(systemName: "chevron.right.circle")\n                        .imageScale(.large)\n                        .rotationEffect(.degrees(showDetail ? 90 : 0))\n                      \n//                        .animation(nil)//关闭旋转动画\n                        \n                        .scaleEffect(showDetail ? 1.5 : 1)\n                        .padding()\n                       \n                       \n//              规模效应          视图从隐藏到展示时，让切换按钮变大1.5倍\n//                        .animation(.easeInOut)\n//                        .animation(.spring())//easeInOut改为spring(),轻松进出改为\n////                    春天 （）\n//                    给显示/隐藏切换的箭头按钮添加旋转动画\n                }\n            }\n\n            if showDetail {\n                HikeDetail(hike: hike)\n            }\n        }\n    }\n}\n\nstruct HikeView_Previews: PreviewProvider {\n    static var previews: some View {\n        VStack {\n            HikeView(hike: hikeData[0])\n                .padding()\n            Spacer()\n        }\n    }\n}\n
						
				第二节 把视图的状态改态转化成动画效果
					已经学会了给单个视图添加动画的方法，现在可以学习怎么在视图的状态发生改变时添加动画效果。当用户点击按钮时会切换showDetail【查看详细】状态的值，在视图变化过程中添加动画效
						
					步骤
						步骤1 把showDetail.toggle()包裹在withAnimation函数调用块中。showDetail的改变影响了视图HikeDetail和详情切换按钮，在显示/隐藏详情的过程中都有了过滤动画效果。
						with_animation block
							
						放慢动画速度，可以观察SwiftUI动画在被中断下是怎么运作的
						步骤2 给withAnimation传入一个时长4秒的基本动画参数.easeInOut(duration:4)，可以指定动画过程时长，给withAnimation传入的动画参数与.animation(_:)修改器可用参数一致。
						with animation duration block
							
						步骤3 在动画过程进行中点击按钮切换视图状态，查看对应的动画被中断时的效果
						with animation interrupt
							
				第三节 定制视图转场动画
					默值情况下，视图离屏和入屏时的动画效果是渐隐/渐现， 这个默认的转场效果可以使用transition(_:)修改器进行定制
						
					步骤
						步骤1 给HikeView视图（远足视图）添加transition(_:)（过渡（_：））修改器，并定制转场参数为.slide（。滑动），转场动画为滑入/滑出
							
						步骤2 可以把滑入/滑出这种转场动画封装起来，方便其它视图复用同样的转场效果
							
						步骤3 在moveAndFade转场效果的定义中使用move(edge:)，让滑入/滑出从屏幕的同一边进行
							
						步骤4 使用asymmetric(insertion:removal:)修改器来定制视图显示/消失时的转场动画效果
							
				第四节 组合复杂的动画效果
					点击图表下面的三个按钮，会在三个不同的数据集间进行切换并展示。本节中会使用组合动画，让图表在不同数据集间切换时的转换动画流畅自然。
						
					步骤
						步骤1 把showDetail（查看详细）的默认值改为true，并把HikeView（远足视图）的预览模式视图固定在画布上。这样可以在编辑其它文件时，依然看到动画效果的变化。
						pin canvas（大头画布）
							
						步骤2 在HikeGraph.swift（远足图。 迅速）中定义了一个新的波动动画，并把它与滑入/滑出动画一起应用到图表视图上。
						hike graph ripple(远足图波纹)
							
						步骤3 把动画切换为弹簧动画(spring)（春天），并设置弹簧阻尼系数为0.5，动画过程中产生了逐渐回弹效果
						spring animation(弹簧动画)
							
						步骤4 加速弹簧动画的执行速度，缩短切换图表的时间
						spring animation speed(弹簧动画速度)
							
						步骤5 以当条形在图表中的位置为参数，添加延迟效果，图表中的每个条形会顺序动起来
						spring animation index based delay(基于弹簧动画索引的延迟)
							
						步骤6 观察一下自定义波动(rippling)效果是怎么作用在视图转场中的
		3 应用设计与布局
			六 组合复杂用户界面
				第一节 添加一个首页视图
					已经创建了所有在Landmarks应用中需要的视图，现在给应用创建一个首页视图，把之前创建的视图整合起来。首页不仅仅包含之前创建的视图，它还提供页面间导航的方式，同时也可以展示各种地标信息。
						
					步骤
						步骤1 创建一个名为CategoryHome.swift（分类首页）的自定义视图文件
						section 1 step 1\n第 1 节 第 1 步
							
						步骤2 把应用的场景代理(scene delegate场景委托)的根视图从之前的地标列表视图更改为新创建的首页视图。现在应用启动后的每一个页面就是首页了，所以还需要添加从首页导航跳转到其它页面的方法。
						section 1 step 2
							
						步骤3 添加NavigationView（导航视图），这个NavigationView将会容纳Landmarks（地标）应用中其它不同的视图。配合使用NavigationView、NavigationLink（导航视图、导航链接）及相关的修改器，就可以构建出应用的页面间导航结构
						section 1 step 3
							
						步骤4 设置导航栏标题为Featured（精选）
						section 1 step 4
							
				第二节 创建地标类别列表
					Landmarks应用为了便于用户浏览各种类别的地标，将地标按类别竖向排列形成列表视图，对于每一个类别内的具体地标，又把它们按照水平方向排列，形成横向列表。组合使用垂直栈(vertical statck)和水平栈(horizontal stack)并给列表添加滚动
						section 2
							
					步骤
						步骤1 使用Dictionary（字典）结构体的初始化方法init(grouping:by:)，【在里面 分组】把地标数据的类别属性category【类别】传入作为分组依据，可以把地标数据按类别分组。工程文件中已经为每一个地标样本数据预定义了类别。
						section 2 step 1
							
						步骤2 使用List显示地标数据的类别。Landmark.Category（地标.类别）是枚举类型，它的值标识列表中每一种类别，可以保证类别不会有重复定义
						section 2 step 1
							
				第三节 添加针对单个类别的地标行列表
					Landmarks应用对每个类别下的地标采用横向滑动的行进行展示。添加一个新的视图类型用来表示这样一个地标行，然后使用这个新创建的行类型具体展示某一具体类型上的所有地标。
						
					步骤
						步骤1 定义一个新的视图类型，用来展示地标类别行的内容。新建行视图需要存放地标具体类别的展示数据
							CategoryRow.swift（类别行）并定义一个新的自定义视图CategoryRow用来存放分类行的内容。
						section 3 step 1
							
								struct CategoryRow: View {\n    var categoryName: String\n    var items: [Landmark]\n    \n    var body: some View {\n        Text(self.categoryName)\n            .font(.headline)\n    }\n}\n\nstruct CategoryRow_Previews: PreviewProvider {\n    static var previews: some View {\n        CategoryRow(categoryName: landmarkData[0].category.rawValue, items: Array(landmarkData.prefix(4)))\n    }\n}
						步骤2 更新CategoryHome.swift（分类首页）的代码，把地标类别信息传给新建的行视图类型
							  List {\n                ForEach(categories.keys.sorted(), id: \.self) { key in\n                    CategoryRow(categoryName: key, items: self.categories[key]!)\n                }\n            }
						section 3 step 2
							
						步骤3 在CategoryRow.swift中使用一个HStack展示类别下的地标内容
						section 3 step 3
							
								var body: some View {\n        HStack(alignment: .top, spacing: 0) {\n            ForEach(self.items) { landmark in\n                Text(landmark.name)\n            }\n        }\n    }\n}
						通过使用框架frame(width:height:)指定高度并将stack嵌套进一个滚动视图让行视图的内容有更合理的空间。
						section 3 step 4
							
					
					代码
						\nimport SwiftUI\n//用来存放分类行的内容\nstruct CategoryRow: View {\n    \n    var categoryName:String//类别名称\n    var items:[Landmark]//变量项目\n    \n    var body: some View {\n        VStack(alignment: .leading) {\n            Text(self.categoryName)\n                .font(.headline)\n                .padding(.leading,15)\n                .padding(.top,5)\n        }\n        \n        ScrollView(.horizontal,showsIndicators:false){\n            HStack (alignment: .top,spacing: 0){//对齐：.top，间距：0）\n                ForEach(self.items){//为每个\n                    Landmark in\n                    Text(Landmark.name)\n                }\n        }\n        }\n       \n        \n//            Text(self.categoryName)\n//                .font(.headline)\n//        }\n//        /**文本（自我。类别名称）\n//         . 字体（标题）\n//}*/\n//    }\n\n        .frame(height: 185)\n    }\n}\n\nstruct CategoryRow_Previews: PreviewProvider {\n    static var previews: some View {\n        CategoryRow(categoryName: landmarkData[0].category.rawValue, items: Array(landmarkData.prefix(4)))\n        /**类别行\n         类别名称：地标数据[0]。\n            类别 。 原始值，项目：数组（地标数据。前缀（3）））*/\n    }\n}\n
				第四节 组合首页
					Landmarks应用的首页在用户点击查看地标详情前需要先把地标的一些简单信息展示出来。复用之前创建的视图构建具体某一类别地标的行视图
						
					步骤
						步骤1 在CategoryRow.swift文件中，与CategoryRow类型并列，创建一个新的自定义视图类型CategoryItem（类别项目），用这个新的视图类型替换CategoryRow的地标名称Text控件
							struct CategoryItem: View {\n    var landmark: Landmark\n    var body: some View {\n        VStack(alignment: .leading) {\n            landmark.image\n                .resizable()\n                .frame(width: 155, height: 155)\n                .cornerRadius(5)\n            Text(landmark.name)\n        }\n        .padding(.leading, 15)\n    }\n}\n\n\nstruct CategoryRow: View {\n    var categoryName: String\n    var items: [Landmark]\n// 省略部分代码\n                HStack(alignment: .top, spacing: 0) {\n                    ForEach(self.items) { landmark in\n                        CategoryItem(landmark: landmark)\n                    }\n                }
						section 4 step 1
							
						步骤2 在CategoryHome.swift中，添加一个名为FeaturedLandmarks【特色地标】的简单视图，这个视图用来显示地标数据中isFeatured属性为真的那些地标。在之后的教程中，会把FeaturedLandmarks这个视图修改成一个交互式轮播图。目前，这个视图仅仅展示一张缩放和剪裁后的地标图片。
							struct FeaturedLandmarks: View {\n    var landmarks: [Landmark]\n    var body: some View {\n        landmarks[0].image.resizable()\n    }\n}\n\nstruct CategoryHome: View {\n// 省略部分代码\n    \n    var featured: [Landmark] {\n        landmarkData.filter { $0.isFeatured }\n    }\n    \n    var body: some View {\n        NavigationView {\n            List {\n                FeaturedLandmarks(landmarks: featured)\n                    .scaledToFill()\n                    .frame(height: 200)\n                    .clipped()\n                \n                ForEach(categories.keys.sorted(), id: \.self) {
						section 4 step 2
							
						步骤3 把视图的边距设置为0，让展示内容可以尽量贴着屏幕边沿
							      .frame(height: 200)\n                    .clipped()\n                    .listRowInsets(EdgeInsets())\n                \n                ForEach(categories.keys.sorted(), id: \.self) { key in\n                    CategoryRow(categoryName: key, items: self.categories[key]!)\n                .listRowInsets(EdgeInsets())
						section 4 step 3
							
				05 在各模块之间添加导航
					现在所有类别的地标都可以在首页视图中展示出来，用户还需要能够进入应用其它页面的方法。使用页面导航和相关API来实现用户从应用首页到地标详情页、收藏列表页及用户个人中心页的跳转。\n\n
						
					步骤
						步骤1 在CategoryRow.swift中，把CategoryItem【类别项目】视图包裹在NavigationLink【导航链接】视图中。CategoryItem这时做为跳转按钮的内容，destination【目的地】指定点击NavigationLink按钮时要跳转的目标视图。
						section 5 step 1
							
						步骤2 使用renderingMode(_:)【渲染模式】和foregroundColor(_:)【前景色】这两个属性修改器来改变地标类别项的导航样式。做为NavigationLink标签的CategoryItem中的文本会使用Environment【环境】中的强调颜色，图片可能以模板图片的方式渲染，这些都可以使用属性修改器来调整，达到最佳效果。
						section 5 step 2
							
						步骤3 在CategoryHome.swift【类别首页】中，添加一个模态展示的用户信息展示页，点击了用户图标时弹出展示。当状态showProfile【显示配置文件/简介】被置为true时，展示用户信息页，当showProfile【展示简介】状态置为false时，用户信息页消失。
						section 5 step 3
							
						步骤4 在导航条上添加一个按钮，用来切换showProfile状态的值：true或者false
						section 5 step 4
							
						步骤5 在CategoryHome.swift中添加一个跳转链接，点击时跳转到全部地标的筛选页面。
						section 5 step 5
							
						步骤6 把【地标清单】LandmarkList.swift中的把包裹地标列表视图的NavigationView【导航视图】移动到对应的预览视图中。因为在应用中，LandmarkList总是会被展示在CategoryHome.swift定义的导航视图中。
						section 5 step 6
							
				检查是否理解
					
					
					
						
			七 玩转UI控件（个人主页）
				在Landmarks应用中，用户可以创建一个简介来描述他们自已的个人情况。为了让用户可以编辑自己的简介，我们需要添加一个编辑模式并设计一个偏好设置界面。\n\n这里使用多种通用控件来展示用户的各种数据，并在用户保存他们所做的数据修改时更新地标数据模型。
					检查是否理解
						问题1 编辑状态改变时，怎样更新一个视图，例如，当用户编辑了用户简介信息后点击完成按钮的情况下，是怎么更新一个视图的
							
						
							java泛型
						
				第一节 展示用户简介
					Landmarks应用在本地存储了一些配置和用户偏好设置。在用户编辑这些数据前，会被展示在一个没有编辑按钮的概要视图上
						
					步骤
						步骤1 在项目文件导航栏的Landmarks文件组下面新建一个名为Profile[【轮廓】的文件组，并在这个新建的文件组下面添加一个新视图ProfileHost【简介主机】, 这个新视图包含一个TextView【文本视图】，用来展示用户名称。ProfileHost将会展示静态概要信息，同时支持编辑模式
						secion 1 step 2
							
						步骤2 用步骤1创建的ProfileHost替换Home.swift中的静态文本Text视图。现在主页中的profile【轮廓】按钮点击时可以调起一个用户简介页面了
						secion 1 step 2
							
						步骤3 创建一个新的视图命名为ProfileSummary【资料概要】，它会持有一个Profile实例，并显示一些用户的基本信息。Profile概要视图持有一个Profile对像的原因是，因为它的父视图ProfileHost管理着视图的状态，它不能与Profile进行绑定。
						secion 1 step 3
							
						步骤4 更新ProfileHost【简介主机】文件，显示新的概要视图
						secion 1 step 4
							
						步骤5 创建一个名为HikeBadge【远足徽章】的新视图，这个新视图由Badge视图和一些描述性文字构成。Badge仅仅是一个图形，在HikeBadge视图中的文本与accessibility(label:)【可访问性（标签：）】属性修改器一起，可以让这个徽章对用户更加清晰。注意frame(width:height:)【框架（宽度：高度：）】的两种不同的用法用来配置徽章以不同的缩放尺寸显示。
						secion 1 step 5
							
						步骤6 更新ProfileSummary文件，添加几个不同的徽章代表用户得到的不同徽章
						secion 1 step 6
							
						步骤7 把HikeView包含在ProfileSummary页面中后，就完成了第一节的实践内容了。
						secion 1 step 7
							
				第二节 添加编辑模式
					用户需要能够在浏览模式和编辑模式之间进行切换来查看或者修改用户简介的信息。通过在ProfileHost【简介主机】上添加一个Edit Button【编辑按钮】，然后创建一个用来编辑简介信息的页面。
						
					步骤
						步骤1 添加一个Enviornment 环境 视图属性，用来使用\.edit模式。可以使用这个属性来读写当前编辑模式。
						secion 2 step 1
							
						步骤2 创建一个编辑按钮，可以切换编辑模式
						secion 2 step 2
							
						步骤3 更新UserData类，包含一个Profile 轮廓  实例，即使用户简介页面消失后也可以存储编辑后的信息
						secion 2 step 3
							
						步骤4 从环境变量中读取用户简介信息，并把数据传递给ProfileHost 简介主机 视图的控件上进行展示。为了在编辑状态下修改简介信息后确认修改前避免更新全局状态(例如在编辑用户名的过程中)，编辑视图在一个备份属性中进行相应的修改操作，确认修改后，才把备份属性同步到全局应用状态中。
						secion 2 step 4
							
						步骤5 添加一个条件视图，可以用来显示静态用户简介视图或者是用户简介视图的编辑模式。当前的编辑模式只支持静态文本框的编辑。
						secion 2 step 5
							
				第三节 定义简介编辑器
					用户简介编辑器包含几个单独的控件用来修改对应简介信息。在简介中，一些项例如徽章是不可以编辑修改的，所以它们不会出现在简介编辑器中。为了保持简介在编辑模式和浏览模式的一致性，需要按照简介页面各项相同的顺序进行添加。
						
					步骤
						步骤1 创建一个名为ProfileEditor 个人资料编辑器 的新视图，并绑定用户简介中的草稿。视图中的第一个控件是TextField 文本域 ，用来更新用户名字段值。创建TextField时要提供一个标签和一个绑定字符串。
						secion 3 step 1
							
						步骤2 更新ProfileHost 简介主机 中的条件内容，让它包含条件编辑器并把简单的绑定关系传递给简介编辑器。现在当你点击Edit 编辑 按钮，简介视图就会变成编辑模式了。
						secion 3 step 2
							
						步骤3 添加一个 切换开关 ，用来设置用户是否接收相关地标事件的推送通知。这个Toggle 切换 控件打开和关闭正好对应着布尔值的true或false。
						secion 3 step 3
							
						步骤4 把一个Picker 选择器 和一个Text放在VStack结构里，让这个地标可以选择不同季节。
						secion 3 step 4
							
						步骤5 最后，在 季节图片选择器 下方添加一个DatePicker 日期选择器，用来修改地标的目标浏览日期
						secion 3 step 5
							
				第四节 延迟编辑传播
					为了让编辑的数据在在用户退出编辑模式之后才生效，我们在编辑的时候使用档案的一个拷贝，然后在用户退出编辑模式的时候将拷贝中的数据赋值给源数据。
						
					步骤
						第一步\n在ProfileHost 简介主机 中添加一个取消按钮。\n\n与EditButton 编辑按钮 中的Done  完毕 状态下的按钮不同，取消按钮不会在它的闭包代码中将编辑过的数据应用到实际档案数据中。
						
						第二步\n在ProfileHost 简介主机 文件中，对编辑器视图应用onAppear(perform:) 出现时（执行:) 修饰器和onDisappear(perform:) 消失时（执行:) 修饰器，为编辑视图提供正确的档案数据并在用户点击完成按钮后将更新的数据持久化。\n\n如果没有这一步，下次进入编辑器显示的还是旧数据。
						
		4 框架集成\n混合使用SwiftUI框架和其它UI框架
			八 与UIKit交互
				简介
					SwiftUI可以无缝地与现有的UI框架在所有苹果平台运行。例如，我们可以将UIKit【用户界面套件】视图和视图控制器嵌套进SwiftUI的视图，或者是反过来。\n\n我们在这个教程学习如何将主页面中的特别地标部分嵌套在UIPageViewController 【UI 页面视图控制器 】和UIPageControl 】UI 页面控制】 中。我们用UIPageViewController【 UI 页面视图控制器 】显示SwiftUI跑马灯视图，并使用状态变量和数据绑定来协调所有界面之间的数据更新。
				第一节 创建一个用来展示UIPageViewController【UI 页面视图控制器】的SwiftUI视图
					
					步骤
						步骤1 创建一个新的SwiftUI视图文件，命名为【页面视图控制器】PageViewController.swift，并且声明PageViewController类型遵循UIViewControllerRepresentable【UI 视图控制器可表示】。这个页面视图控制器存放一个UIViewController【UI 视图控制器】实例数组，数组中的每一个元素代表在地标滚动过程中的一页视图。
						section 1 step 1
							
							下一步添加UIViewControllerRepresentable协议的两个实现, 目前因为协议方法没有完成实现，会有报错提示。
						步骤2 添加一个makeUIViewController(context:)方法，方法内部以指定的配置（let）创建一个UIPageViewController。SwiftUI会在准备显示视图时调用一次makeUIViewController(context:)方法创建UIViewController实例，并管理它的生命周期。
						section 1 step 2
							
							由于还缺少一个协议方法没有实现，所以目前还是会报错。
						步骤3 添加updateUIViewController(_:context:)【更新 UI 视图控制器（_：上下文 :)】方法，这个方法里调用setViewControllers(_:direction:animated:)方法【设置视图控制器（_：方向：动画：）】展示数组中的第一个视图控制器
						section 1 step 3
							
						创建另一个SwiftUI视图展示遵循UIViewControllerRepresentable协议的视图
						步骤4 创建一个名为PageView.swift的视图，声明一个PageViewController作为子视图。初始化时使用一个视图数组来初始化，并把每一个视图都嵌入在一个UIHostingController【UI 托管控制器】中。UIHostingController是一个UIViewController的子类，用来在UIKit环境中表示一个SwiftUI视图。
						section 1 step 4
							
						步骤5 更新预览视图，并传入视图数组，预览视图就会开始工作了
						section 1 step 5
							
						步骤6 在继续下面的步骤前，先把PageView的预览视图固定住，以避免在文件切换时不能实现预览到PageView的改变。
						section 1 step 6
							
				第二节 创建视图控制器的数据源
					短短几个步骤就做了很多事，PageViewController【页面视图控制器】使用UIPageViewController【UI 页面视图控制器】去展示来自SwiftUI内容。现在是时候添加挥动手势进行页面之间的翻动了。\n一个展示UIKit视图控制器的SwiftUI视图可以定义一个Coordinator【协调员】类型，这个Coordinator类型由SwitUI管理，用来作为视图展示的环境
						
					步骤
						步骤1 在PageViewControlelr中定义一个嵌套类型Coordiantor。SwiftUI管理UIViewController Representable【有代表性的】类型的coordinator，并在调用方法时把它作为环境的一部分。
							
						步骤2 在PageView Controller中添加另一个方法，创建coordinator。SwiftUI在调用makeUIViewController(context:)【制作 UI 视图控制器（上下文：）】前会先调用makeCoordinator()方法，因此在配置视图控制器时是可以访问到coordiantor对象的。可以使用coordinator为实现通用的Cocoa模式,例如：代理模式、数据源以及目标-动作。
							
						步骤3 让Coordinator类型添加UIPageViewControllerDataSource【UI 页面视图控制器数据源】协议遵循，并且实现两个必要方法。这两个必要方法会建立起视图控制器之间的联系，因此可以实现页面之前的前后切换。
							
						步骤4 把coordiantor作为UIPageViewController的数据源
							
						步骤5 打开实时预览，并测试一下前后页面切换的功能是否正常
							
				第三节 在SwiftUI视图的状态下跟踪页面
					如果要添加一个自定义的UIPageControl控件，就需要一种方式能够在PageView中跟踪当前展示的页面。这就需要在PageView中声明一个@State【@状态】属性，并传递一个针对该属性的绑定关系给PageViewController视图，在PageViewController中通过绑定关系更新状态属性，来反映当前展示的页面。
						
					步骤
						步骤1 在PageViewController中添加一个绑定属性currentPage【当前页面】。除了使用关键字@Binding【@捆绑】声明属性为绑定属性外，还需要更新一下函数setViewControllers(_:direction:animated:)【设置视图控制器（_：方向：动画：）】，给它传入currentPage绑定属性
							
						步骤2 在PageView中声明@State变量，并在创建PageViewController时把绑定属性传入。注意使用$语法创建一个针对状态变量的绑定关系。\n\n
							SwiftUI 基础篇之 @State
								通过使用@State，我们可以在未使用 mutating 的情况下修改结构中的值\n当状态值发生变化后，视图会自动重绘以反应状态的变化。
								在 SwiftUI 中，视图是由数据(状态)驱动的。每当视图在创建或解析时，都会为该视图和该视图中使用的状态数据之间创建一个依赖关系，每当状态的信息发生变化，有依赖关系的视图会马上翻译出这些变化并重绘。
						步骤3 通过改变PageView视图中的currentPage初始值来测试绑定关系是否正常生效。也可以做一个测试按钮，点击按钮时让第二个页面展示出来
						步骤4 添加一个TextView控件来展示状态变量currentPage的值，拖动页面切换时观察TextView上的值，目前不会发生变化。因为PageViewController内部没有在切换页面的过程中更新currentPage的值。
						步骤5 在PageViewController.swift中让coordinator作UIPageViewController的代理，并添加pageViewController(_:didFinishAnimating:previousViewControllers:transitionCompleted completed: Bool) 【页面视图控制器（_：完成动画：上一个视图控制器：转换完成完成：布尔）】方法。因为SwiftUI在页面切换动画完成时会调用这个方法，这样就可以这个方法内部获取当前正在展示的页面的下标，并同时更新绑定属性currentPage的值。
						步骤6 coordinator除了是UIPageViewController数据源外，再把它赋值为UIPageViewController的代理。由于绑定关系是双向的，所以当页面切换时，PageView视图上的Text就会实时展示当前的页码。
				第四节 添加一个自定义PageControl
					我们已经为包裹在UIViewRepresentable【UI 视图可表示||有代表性的】视图中的子视图上添加了一个自定义UIPageControl【UI 页面控制】\n
						
					步骤
						步骤1 创建一个新的SwiftUI视图，命名为PageControl【页面控件】.swift，并使用PageControl类型遵循UIViewRepresentable【有代表性的】协议。UIViewRepresentable和UIViewControllerRepresentable类型有相同的生命周期，在UIKit类型中都有对应的生命周期方法。
						步骤2 在PageView中用PageControl替换Text,并把VStack换成ZStack。因为总页数和当前页面都已经传入PageControl，所以PageControl已经可以正确的显示。
						下一步要处理PageControl与用户的交互，让它可以被用户点击任意一边进行页面间的切换。
						步骤3 在PageControl中创建一个嵌套类型Coordiantor【协调员】，添加一个makeCoordinator()方法创建并返回一个coordinator实例。因为UIControl子类(包括UIPageControl)使用Target-Action【目标行动】模式，Coordinator实现一个@objc方法来更新currentPage绑定属性的值。
						步骤4 把coordinator【协调员】作为PageControl【页面控件】值改变事件的目标处理器，并指定updateCurrentPage(sender:)【更新当前页面（发件人：）】方法为处理函数
						步骤5 现在就可以尝试PageControl的各种交互来切换页面，PageView展示了SwiftUI和UIKit视图如何混合使用。
				检查是否理解
					
					
			九 创建watchOS应用
			十 创建macOS应用
	SwiftUI特点
		只需要描述一次布局
			声明式描述任何状态下的视图内容和布局。SwiftUI知道视图何时发生状态改变，并及时刷新对应状态下的视图内容。
				各种编程语言都差不多
				//类的继承\n//swift是一个单继承关系，和多协议（多接口）
					import Cocoa\n\n//协议protocol （Java接口interface） 主要描述属性或方法规定的一个样子（抽象）\n\n//协议protocal，相当于API\nclass TestClass\n{\n    \n}\nprotocol Protocol1 {\n    var value1:String {set get}\n    func paly1() -> String\n    \n}
		构建可复用组件\n（多次？多位置？）
			把多个目标单一的小视图组合成功能复杂的大视图进而组合成复杂的用户界面。同时自定义的视图还可以在不同的苹果平台设备应用开发中复用。
				
				特征图片\n可调整大小\n方面比率\n内容模式\n合身\n覆盖\n文本叠加
				//链式调用方式：return this\n   
		简化动画效果实现
			创建流畅的动画效果仅仅需要添加一个方法调用就可以完成。\n
				
		Xcode中实时预览
			不需要实际运行应用就可以完成设计、构建和测试工作。使用交互式的预览功能来测试你开发的控件和页面布局。
