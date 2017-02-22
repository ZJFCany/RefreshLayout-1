# QRefreshLayout
一个下拉刷新上拉加载更多的Android自定义布局

##Change Log
 ```
v1.2.1
1、修复下拉拖动时会错误的触发TargetView点击事件的BUG
2、修复快速点击TargetView会导致TargetView的Selector无法正常显示的BUG
3、修复上拉加载更多结束后偶尔会导致TargetView无法滑动的BUG
4、修复了TargetView为TextView时无法触发下拉刷新的BUG

v1.2.0
1、对QLoadView代码进行重构以支持更丰富的下拉效果，不再支持1.1.x及以下版本的QLoadView及自定义的子类
2、新增加了两个QLoadView实现类：MaterialHeaderView(FooterView)、MateriaBlackHeaderView(FooterView)
```
    
![](https://github.com/qstumn/QRefreshLayout/blob/master/demo.gif?raw=true)       ![](https://github.com/qstumn/QRefreshLayout/blob/master/demo2.gif?raw=true)


##how to use:
###1. gradle
```
    compile 'q.rorbin:QRefreshLayout:1.2.1'  
```
###2. xml
```xml
    <q.rorbin.qrefreshlayout.QRefreshLayout
        android:id="@+id/refreshlayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
        
        <ListView 
            android:id="@+id/listview"
            android:layout_width="match_parent"
            android:layout_height="match_parent"/>
            
    </q.rorbin.qrefreshlayout.QRefreshLayout>
```

###3. code
  
   如果需要上拉加载更多功能，请调用以下方法
```java
  mRefreshLayout.setLoadMoreEnable(true);
```

   设置监听 
```java
    mRefreshLayout.setRefreshHandler(new RefreshHandler() {
    
            @Override
            public void onRefresh(QRefreshLayout refresh) {
                do something...
                mRefreshLayout.refreshComplete();
            }
            
            @Override
            public void onLoadMore(QRefreshLayout refresh) {
                do something...
                mRefreshLayout.LoadMoreComplete();
            }
        });
```
  如果你想自定义头部或者尾部的View，只需要将你的View继承自QLoadView即可
  
```java
  public class CustomView extends QLoadView
```
  
   然后再设置进布局
  
```java
  mRefreshLayout.setHeaderView(new CustomView());
  mRefreshLayout.setFooterView(new CustomView());
```
  
   QLoadView已有三种实现类供您选择使用，分别为：HeaderView(FooterView)、MaterialHeaderView(MaterialFooterView)、MateriaBlackHeaderView(MateriaBlackFooterView)，QRefreshLayout默认设置为HeaderView
 
###4. 属性说明
 
 xml | code | 说明
 --- | --- | ---
 app:resistance | setResistance | 设置下拉阻力(范围0f~1f)
 
 
#LICENSE
```
Copyright 2016, RorbinQiu

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
