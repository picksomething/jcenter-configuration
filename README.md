JCenter-configuration
=====================

为了方便配置大家讲自己开源的库上传到JCenter，特意把其中配置gradle文件时一些公用的配置项单独提取出来，大家在配置的时候，直接引用这些配置项，然后再配置一些自己的私有信息就可以了，私有信息主要就是上传的库的信息和开发者信息，已经JCenter仓库的信息。

Usage
=====

- 在要上传的库所在的module模块的build.gradle文件中加入如下两句：

```groovy
apply from:'https://raw.githubusercontent.com/picksomething/jcenter-configuration/master/install-template.gradle'
apply from:'https://raw.githubusercontent.com/picksomething/jcenter-configuration/master/bintray-template.gradle'
```

- 在最外层Project的build.gradle所在的目录新建一个data.gradle
- 在新建的data.gradle文件中加入如下配置信息：

```
ext {
    bintrayRepo = 'picksomething' //bintray上的仓库名，随便填，并不一定为maven，只要和你在bintray上创建的仓库的名字一致就好。
    bintrayName = 'slidingtabindicator' //bintray上的项目名，也是随便填，很多人教程都说要和你在仓库里面新建的package名字一样，实时情况是如果你在仓库里自己没有新建package，你上传的时候也会自动按照这个名字在你仓库里新建对应的package，所以没有必要现在仓库里面新建，如果你已经新建了，那就保持一致即可。

    publishedGroupId = 'cn.picksomething' //最终别人要依赖你的项目的时候，形式就是publishedGroupId:artifact:libraryVersion，所以该怎么填你很清楚了吧，最好是唯一。
    libraryName = 'slidingtabindicator'//这个最好和artifact一样
    artifact = 'slidingtabindicator'//这个必须要和library module的名字一样，我之前不一样，上传的时候一直出错。

    libraryDescription = 'Android Library to add simple sliding tab with indicator'

    siteUrl = 'https://github.com/picksomething/sliding-tab-indicator'//项目地址
    gitUrl = 'https://github.com/picksomething/sliding-tab-indicator.git'//git专用地址

    libraryVersion = '1.0.0'

    developerId = 'picksomething'//随
    developerName = 'picksomething'//便
    developerEmail = 'zzucaobin@gmail.com'//填

    licenseName = 'The Apache Software License, Version 2.0'
    licenseUrl = 'http://www.apache.org/licenses/LICENSE-2.0.txt'
    allLicenses = ["Apache-2.0"]
}
```
> 需要注意的是默认`bintray.user`和`bintray.key`这两个字段是从项目最外层的`local.properties`里面读取的，所以记得在`local.properties`里面配置，这个文件不用上传，在`.gitignore`里面忽略一下即可，当然如果你在github上面新建代码仓库的时候选择添加`.gitignore`且项目类型选择Android，那么这个`local.properties`文件默认就会自动忽略的。

License
=======

    Copyright 2017 picksomething

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.