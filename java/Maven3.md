Apache Maven3(Note:Maven3)

1.是什么:
	
		a.java语言开发的工具软件包
		b.用于从组织项目结构－>项目发布整个过程构建的工具
		c.同类:Make,Ant+lvy,Gradle
		
		
2.干什么:

		1.统一项目目录结构(约定优于配置,可以在超级pom(M2_HOME/lib/底下修改)里面修改，但是建议不要改，开发人员遵循一致的约定) 
		2.统一项目构建过程(通过插件和插件的生命周期命令来处理构建的生命周期)
		3.依赖包的和包版本的统一管理(自身主项目只处理首层依赖,次层依赖(依赖的依赖)Maven会在依赖包的pom.xml中自己去解析寻找)
		4.信息管理（统一生成项目网站和报表 site:deploy,通过生命周期的插件来完成）
		
		过程:产生包结构->编译->测试->持续整合->依赖->报告->site
	
	
3.核心概念:

		POM(pom.xml)
		Coordinates(GroupId ArtifactId Version)
		ProjectLifecycle & PlugIn & Goal
		Repositories & Dependency Management System


4.传统工具对比：
 
         Ant  	过程		随意		程序化		无生命周期
         
         Maven  对象		约定		声明			有生命周期
   		 		 				
		 IDE	手动		依赖IDE	不可见		不可见
		 
		 
5.安装和目录结构:

		download Maven3
		
		EXPORT M2_HOME={SETUPED_MAVEN_ROOT_PATH}
		
		EXPORT PATH=$M2_HOME/bin:$PATH  
		
		mvn －v will: 
					a.gen ~/.m2 folder & ~/.m2/repository & ~/.m2/setting.xml
					b.download plugin jar
					c.Maven中所有和项目生命周期相关的命令都是插件(compile,test,jar...)
		
		
		
		~/.m2/repository的目录结构管理规则是  ~/.m2/repository/G/A/V／G-A-V*.jar

  
		目录结构:
        M2_HOME/
        		bin/	mvn等可执行文件 shell ...
        		boot/	plexus-classworlds classloader 代替默认的jvm的classloader ...
        		conf/   setting.xml ...		
        		lib/	maven自身的jar和依赖的libs(*.jar) 
        				super pom(中央仓库的地址super pom中也配置了一份,
        				在maven-model-builder.jar中) ...  		
        		
        
        
        cp M2_HOME/conf/setting.xml to   ~/.m2/  then use this copied setting.xml:
 
        可在setting.xml中配置节点Mirror(中央仓库地址),也可在项目pom中配置中央仓库地址
		可在setting.xml中配置节点Proxies(上网代理)
        

6.命令行生成一个Maven模版项目：

		cd workspace
		mvn  archetype:generate -DgroupId=com.huanx.ProjectName 
								-DartifactId= ProjectName-Module 
								-DpackageName=a.b.c
		结构:
		ProjectName-Module(n)/
             			   	  src/main/java
             			   	  				/a/b/c/*.java
	    	 			  	  src/main/resources
	    	 		      	  src/test/java		 
	    	 		      	  				/a/b/c/*Test.java
	    	 		      	  src/test/resources	 
             		     	  pom.xml
             		     	  
        ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
        由于历史,Maven编译插件的source和target默认是1.3的编译器，新编译器的新特性请设置高版本的compiler source和target(最新版本可能没有这个问题)
        <build>
 			<plugins>
		        <plugin>
						<artifactId>maven-compiler-plugin</artifactId>
						<version>2.3.2</version>
						<configuration>
							<source>1.8</source>
							<target>1.8</target>
							<encoding>UTF8</encoding>
						</configuration>
				</plugin>
			<plugins>
		</build>	
			
        ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝    
        
        
        ===＝＝＝＝＝＝＝＝＝＝如果需要运行有main方法的类则需要使用插件如下＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝ 		     
        	  
       <build>
 			<plugins> 	  
			        <plugin>  
			        <groupId>org.apache.maven.plugins</groupId>  
			        <artifactId>maven-shade-plugin</artifactId>  
			        <version>2.0</version>  
			        <configuration>  
			          <transformers>  
			         	<transformer implementation = "org.apache.maven.plugins.shade.resource.MainifestResourceTransformer">  
			         	<mainClass>package.HelloWorld</mainClass>  
			         	</transformer>  
			      	  </transformers>  
			        </configuration>  
			        <executions>  
			          <execution>  
			            <phase>package</phase>  
			            <goals>  
			              <goal>shade</goal>  
			            </goals>  
			          </execution>  
			        </executions>  
			      </plugin> 
			<plugins>
		<build>	      
             		
      ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
		cd ProjectName-Module(n)
		
		mvn  clean compile     产生classes
		
		mvn  clean test 	   运行测试    
		
		mvn  clean package     产生可用jar or war
		
		mvn  clean install     将jar安装到本地库，其它工程通过GAV可以使用
		
    	=========>
    	
		ProjectName-Module(n)/
             			      src/main/java/
    	   		 		      src/main/resources/
            			      src/test/java/
            		          src/test/resources/
           		  		      pom.xml
           		  		      target(mvn后产生的各种中间产品)/
           		  									      G-A-V.P
           		  									      classes/*.class
	
				
				
				
				
				

7.生命周期
		
		
		生命周期：三套生命周期分别有很多阶段，每套生命周期相互独立
	
		clean:pre-clean,clean,post-clean

		default:validate,init,gem-src,process-src,genres,process-res,compile,gen-test-res,process-test-src,gem-test-res,process-test-res
            test-compile,test,prepare-package,package,pre-integration-test,integration-test,post-integration-test,verify,install,deploy
            
		site:pre-site,site,post-site,site-deploy
		
		周期:插件(1:n)
		
		==========================================
		
		插件:目标(1:n)  compile:compile   compile:testCompile

		mvn命令行就是调用生命周期的目标  mvn clean  deploy site-deploy
										目标    目标      目标
		很多第三方插件 mvn jetty  mvn tomcat


8.坐标：

		G:一个组织底下具体的项目			a.b.c.Project
		A: 一个项目底下具体的模块		ProjectName-Module(n)
		V:版本号						1.0
		P:打包方式					jar war ...
		C:不能自己定义					java-doc java-resource ...
		
		G/A/V/A-V.P(C)


9.仓库：

		
		
		寻找路径:本地仓库->代理仓库(可有可无)->中央仓库
 

10.Maven的UI界面搜索：

		http://repository.sonatype.org	
		http://mvnrepository.com	
 

11.聚合:

			多工程各自作为模块聚合成一个工程，聚合后的各个工程有单独的pom，并在主工程中配置module结点引入子模块，主工程的package是pom。

		    ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
		    <packaging>pom</packaging>
			<modules>
				<module>ProjectName-Module1</module>
				<module>ProjectName-Module2</module>
				<module>ProjectName-Module(n)</module>
			</modules>
		    ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝

		(1)如果子工程在主工程根目录则:
	    	mkdir ProjectName 	
			cd ProjectName 
			mvn  archetype:generate -DgroupId=com.huanx.ProjectName -DartifactId= ProjectName-All -DpackageName=com.huanx.somename
			mdkir ProjectName-Module(n)
			cd ProjectName-Module(n)
			mvn  archetype:generate -DgroupId=com.huanx.ProjectName -DartifactId= ProjectName-Module(n) -DpackageName=com.huanx.somename
			cd ..
			maven clean compile 
	   
			在主工程的pom中配置
		   	＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
			<modules>
				<module>ProjectName-Module1</module>
				<module>ProjectName-Module2</module>
				<module>ProjectName-Module(n)</module>
			</modules>
			＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
		
		
		(2)如果子工程在主工程平行目录则:
	    	mkdir ProjectName 
			cd ProjectName 
			mvn  archetype:generate -DgroupId=com.huanx.ProjectName -DartifactId= ProjectName-All -DpackageName=com.huanx.somename
	    	cd ..
			mdkir ProjectName-Module(n)
			cd ProjectName-Module(n)
			mvn  archetype:generate -DgroupId=com.huanx.ProjectName -DartifactId= ProjectName-Module(n) -DpackageName=com.huanx.somename
			cd ../ProjectName
			maven clean compile 
			
			在主工程的pom中配置
		    ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
			<modules>
				<module>../ProjectName-Module1</module>
				<module>../ProjectName-Module2</module>
				<module>../ProjectName-Module(n)</module>
			</modules>
		    ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝



		(3)多模块聚合的项目构建
			单独:
			mvn clean install -pl ProjectName-Module(1) ProjectName-Module(2) ...
			统一:
			mvn clean install


12.继承：

		在一个模块工程(或主工程)中配置一个通用模版式的pom，其它模块工程继承这个工程的配置，这个模版工程的的package是pom.目的是共享里面的配置比如lib的依赖，就只用在parent的pom中配置了
	
		以上述聚合(1)目录结构为例，如果以ProjectName为parent
		
		ProjectName-Module(n)的pom加入:
	    
	    ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
		<parent>
	    	<artifactId>ProjectName</artifactId>
	    	<groupId>{groupId}</groupId>
	    	<version>{n.n.n}-SNAPSHOT</version>
	    	<relativePath>../pom.xml</relativePath>
	  	</parent>
		＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
	
	
		以上述聚合(2)目录结构为例，如果以ProjectName为parent
		
		ProjectName-Module(n)的pom加入:
		
	    ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
		<parent>
	    	<artifactId>ProjectName</artifactId>
	    	<groupId>{groupId}</groupId>
	    	<version>{n.n.n}-SNAPSHOT</version>
	    	<relativePath>../ProjectName/pom.xml</relativePath>
	  	</parent>
	    ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝

	    不同
		聚合：主知道子，子不知道主，子可以独立，目的是多个相关模块的聚合
		继承：子知道父，父不知道子，父可以独立，目的是消除重复配置
	
	    相同
	    父或主都没有实际内容，package都为pom，很多情况下，主可能是父，比如上面的例子
    



		main+parent作为同一个角色，同时减少配置，同时聚合模块
		
		webapp的finalName设置war的名称
		
		profiles管理不同的配置信息

13.Webapp的Maven特性

	       war/
	        	+META-INF
	        	|
	        	+WEN-INF/
	        	|		 +web.xml
	        	|        |
	        	|		 +libs/*.jar
	        	|		 |
	        	|		 +classes/*.class
	        	+index.html
				
		  将普通pom中修改为:	
		  
		 		 <packaging>war</packaging>
			     <finalName>war包的名称(war包的名称.war)</finalName>
		  
	      容器测试:
     	
     	
 15.pom特性
 
	        变量定义：
	
	 		<properties>
	 			<java-version>1.6</java-version>
				<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
			</properties>
			
	        变量使用：${}
	
		 	差异化配置 Maven Profile(平台，os，开发环境，测试环境，特殊)
 		
 		
 16.site
 
 		
 			mvn site
 		
 		
 		
 
 
 17.自定义插件
 
 


 to be continued ......  依赖，
 		
 		          
