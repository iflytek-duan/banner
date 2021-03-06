[![](https://jitpack.io/v/iflytek-duan/Banner.svg)](https://jitpack.io/#iflytek-duan/Banner)
# Banner
使用ViewPager实现无限轮播效果，实现效果如下：</br>
 ![banner](/images/preview.gif)
# 引入步骤
1. 在build.gradle(Project:xxx)中的repositories内添加：
```
    allprojects {
        repositories {
            ...
            maven { url "https://jitpack.io" }
        }
    }
```
2. 然后在build.gradle(Module:app)中dependencies内添加：
```
	dependencies {
	        ...
	        compile 'com.github.iflytek-duan:Banner:1.0.1'
	}
```

# 更多设置
## 设置Banner页卡点击事件
添加如下代码即可完成Banner页卡点击事件监听：
```java
    banner.setOnPageClickListener(new Banner.OnPageClickListener() {
        @Override
        public void onPageClick(int position) {
        }
    });
```
## 设置画廊效果
在布局中使用以下代码即可设置Banner为画廊模式：<br/>
`app:enable_gallery="true"`<br/>
实现效果如下：<br/>
![Banner_Gallery](/images/preview_gallery.gif)

# 支持属性
<table>
    <tr>
        <td>Name</td>
        <td>Format</td>
        <td>说明</td>
        <td>使用方式</td>
    </tr>
    <tr>
        <td>isAutoLoop</td>
        <td>boolean</td>
        <td>标识是否打开/关闭无限轮播开关，默认为打开状态true</td>
        <td>
            在代码中动态设置：</br>
            banner.setAutoLoop(true);</br>
            在xml中静态配置：</br>
            app:autoLoop="true"
        </td>
    </tr>
    <tr>
        <td>isEnableIndicator</td>
        <td>boolean</td>
        <td>标识是否启用指示器，默认为启用true</td>
        <td>
            在xml中使用：</br>
            app:enable_indicator="true"
        </td>
    </tr>
    <tr>
        <td>isEnableGallery</td>
        <td>boolean</td>
        <td>标识是否启用画廊效果，默认为不启用false</td>
        <td>
            在xml中使用：</br>
            app:enable_gallery="true"
        </td>
    </tr>
    <tr>
        <td>indicatorContainerPadding + L/R/T/B</td>
        <td>integer</td>
        <td>指示器容器填充属性</td>
        <td>
            在xml中使用：</br>
            app:indicator_paddingLeft="10"</br>
            app:indicator_paddingRight="10"</br>
            app:indicator_paddingTop="6"</br>
            app:indicator_paddingBottom="6"
        </td>
    </tr>
    <tr>
        <td>pointMargin + L/R/T/B</td>
        <td>integer</td>
        <td>指示点的Margin属性</td>
        <td>
            在xml中使用：</br>
            app:point_marginLeft="10"</br>
            app:point_marginRight="10"</br>
            app:point_marginTop="6"</br>
            app:point_marginBottom="6"
        </td>
    </tr>
    <tr>
        <td>pointDrawable</td>
        <td>reference</td>
        <td>指示点图片属性</td>
        <td>
            在xml中使用：</br>
            app:pointDrawable="@drawable/point_default_selector"
        </td>
    </tr>
</table>

# 设计思路
- 如何实现无限轮播效果？
在ViewPager的最左侧、最右侧各新增一个页卡，用来映射对应的尾页 / 首页并设置相同的图片内容，达到无缝对
接的效果，设计思路如下图：
 ![banner](/images/banner.png)