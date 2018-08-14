---
layout: post
title: Android-CoordinatorLayout的使用
category: Android
tags: Android 必备
keywords: Android
---

## 要实现顶部是banner 在下面是Tablayout + ViewPager，然后Tablayout自动吸顶

``` java

<android.support.design.widget.CoordinatorLayout
            android:id="@+id/mCoordinator"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:background="@color/color_bar2">

            <android.support.design.widget.AppBarLayout
                android:id="@+id/app_bar_layout"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:background="@color/color_bar2">

                <android.support.design.widget.CollapsingToolbarLayout
                    android:id="@+id/collapsing_toolbar_layout"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    app:contentScrim="@android:color/transparent"//让banner包含的图片一直可见，不然的话会有个渐变的效果
                    app:layout_scrollFlags="scroll">


                    <include layout="@layout/layout_service_banner_item" />

                </android.support.design.widget.CollapsingToolbarLayout>

                <include layout="@layout/layout_sticky_header_view" />


            </android.support.design.widget.AppBarLayout>

            <android.support.v4.widget.NestedScrollView
                android:id="@+id/nsv"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:fillViewport="true"
                android:scrollbars="none"
                app:layout_behavior="@string/appbar_scrolling_view_behavior">

                <android.support.v4.view.ViewPager
                    android:id="@+id/mVp"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:background="@color/color_container"
                    app:layout_behavior="@string/appbar_scrolling_view_behavior" />

            </android.support.v4.widget.NestedScrollView>

        </android.support.design.widget.CoordinatorLayout>

```
我想说一句其实CoordinatorLayout的功能真的很强大。不是我们想的只是滑动视觉效果差而已。可以实现很多炫酷的功能的

[详细请看](https://juejin.im/post/585bb76961ff4b006cc9d5b6)


