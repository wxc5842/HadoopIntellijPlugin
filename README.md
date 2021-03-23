
# IntelliJ plugin for Hadoop

Hadoop-Intellij-Plugin is a plugin on Intellij IDEA. Implemented access and related operations on the Hadoop file system on Intellij IDEA. This includes reading the list of files on the Hadoop file system for display, creating directories in the Hadoop file system, deleting directories, downloading or uploading files, viewing file contents, running Job jobs, supporting international language settings, and so on. Similar plugin with hadoop-eclipse-plugin. Intellij-Plugin-Hadoop interface is roughly as follows:

![](https://github.com/fangyuzhong2016/HadoopIntellijPlugin/blob/master/img-folder/1.jpg)
![](https://github.com/fangyuzhong2016/HadoopIntellijPlugin/blob/master/img-folder/2.jpg)
![](https://github.com/fangyuzhong2016/HadoopIntellijPlugin/blob/master/img-folder/3.jpg)
![](https://github.com/fangyuzhong2016/HadoopIntellijPlugin/blob/master/img-folder/4.jpg)


## How to compile and install ？
- 1、Source code:  
Get the latest source code from https://github.com/fangyuzhong2016/HadoopIntellijPlugin.
- 2、Source compile   
①, The current Intellij plugin for hadoop source code using maven to compile and package, so before compiling to ensure that the installation of JDK1.8 and maven3 or above    
②, Intellij plugin for hadoop plug-in based on IntelliJ IDEA Ultimate 2017.2 version of the development, so need to install IntelliJ IDEA Ultimate 2017 or later  
③, Ready Hadoop related jar package (compilation step is not necessary)    
④, Enter the source directory ../HadoopIntellijPlugin/ modify the pom.xml file, the main modified hadoop version and IntelliJ IDEA installation path, set as follows:  
![](https://github.com/fangyuzhong2016/HadoopIntellijPlugin/blob/master/img-folder/5.jpg)
⑤, the implementation of mvn order:  
First execute   
mvn clean  
Then execute   
mvn assembly:assembly    
After the completion of the compiler in the ... / target / HadoopIntellijPlugin-1.0.zip that is the plug-in installation package, and then installed to IntelliJ

## 3、Intellij plugin for hadoop development environment settings
   As the current use of Maven management Intellij plug-in development more difficult, so if you want to use Intellij modify Intellij plugin for hadoop plug-in code, directly based on the source code to create the Plugin project is not possible, according to IDEA plug-in development model for code engineering settings The
   First create a plugin project in Intellij IDEA, such as HadoopIntellijPlugin, directory organization:
   
 ![](https://github.com/fangyuzhong2016/HadoopIntellijPlugin/blob/master/img-folder/6.jpg)
    Then, the source directory in the ../src/main/java/com folder, copy the development of the plug-in project source ... / src folder, then the source directory .... / src / main / Java / resources folder to the development plug-in project source .... / resources directory, and in the directory, create a lib folder, the Hadoop related jar package, copy in. Finally, set the development of the plug-in project HadoopIntellijPlugin configuration.    
    ①, set the plug-in project expansion of the lib, the hadoop related jar package introduced:
    ![](https://github.com/fangyuzhong2016/HadoopIntellijPlugin/blob/master/img-folder/7.png)
    ②、Plug some UI interface, the use of the IDEA GUI Design drag and drop the design, the interface element to save the corresponding class xml, the compilation process is used in the IDEA library for the compiler, not javac compiler, so in the compiler Process, set the GUI Designer source code generation, if you do not do this step in the development environment in the debug run, no problem, the entire UI interface code from the IDEA framework for dynamic generation insert, but packaged installation, will prompt interface The control failed to instantiate. Set the GUI Designer source code generation, in fact, those UI interface is generated xml file static Java code, insert the source file. In the IDEA settings, make the following settings:
     ![](https://github.com/fangyuzhong2016/HadoopIntellijPlugin/blob/master/img-folder/8.png)
     
## Intellij plugin for hadoop plugin configuration and source code
- 1、 Plug-in source code, the source code organization is as follows:  
    ![](https://github.com/fangyuzhong2016/HadoopIntellijPlugin/blob/master/img-folder/9.jpg)    
      ①, core package, the core package for the plug-in project, the public component library, including the generic UI interface, multi-threaded operation, Hadoop connection set base class, Hadoop file system general operation class, plug-in project settings generic class and other tools    
      ②, fsconnection package, Hadoop file system connection implementation class and connection related configuration implementation class     
      ③, fsobject package, file system object class implementation (for HDFS is the directory tree and file tree node organization to achieve)   
      ④, fsbrowser package, the main interface to achieve plug-ins, including the HDFS file system to read the relevant data display, file system object creation, download, delete, upload and other operations    
      ⑤, globalization package, plug-in multi-language support class⑥, options package, plugin set class⑦, mainmenu package, plug-in main menu operation class     
      
- 2、Plug-in configuration instructions
The plugin is configured in the / resources / directory, including HadoopNavigator_en_US.properties, HadoopNavigator_en_US.properties, plugin.xml.
The HadoopNavigator_en_US.properties file is the English language configuration for the plug-in interface
HadoopNavigator_en_US.properties file for the plug-in interface, the Chinese language configuration
The current plug-in interface language only supports Simplified Chinese and English, other languages, need to make their own language pack. The initial default language for the system is the default language for the operating system. Plugin.xml for the plugin's configuration file
