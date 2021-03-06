EasySlidingTabs
==

![Language](https://img.shields.io/badge/language-Java-EE0000.svg) [![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://github.com/CaMnter/EasyCountDownTextureView/blob/master/LICENSE) 
![Version](https://img.shields.io/badge/version-1.0-8470FF.svg) 
 [ ![Download](https://api.bintray.com/packages/camnter/maven/easyslidingtabs/images/download.svg) ](https://bintray.com/camnter/maven/easyslidingtabs/_latestVersion)   

## Gradle

```Gradle
dependencies {
    compile 'com.camnter.easyslidingtabs:easyslidingtabs:1.0'
}
```


## Blog

 [EasySlidingTabs](http://blog.csdn.net/qq_16430735/article/details/49229189)



## EasySlidingTabs Attribute



```XML
    <declare-styleable name="EasySlidingTabs">
        <attr name="easyIndicatorColor" format="color" />
        <attr name="easyUnderlineColor" format="color" />
        <attr name="easyTabTextColor" format="color" />
        <attr name="easySelectedTagTextColor" format="color" />
        <attr name="easyDividerColor" format="color" />
        <attr name="easyIndicatorHeight" format="dimension" />
        <attr name="easyUnderlineHeight" format="dimension" />
        <attr name="easyDividerPadding" format="dimension" />
        <attr name="easyTabPaddingLeftRight" format="dimension" />
        <attr name="easyTabBackground" format="reference" />
        <attr name="easyScrollOffset" format="dimension" />
        <attr name="easyShouldExpand" format="boolean" />
        <attr name="easyTextAllCaps" format="boolean" />
        <attr name="easyIndicatorDrawable" format="reference" />
    </declare-styleable>
```


## EasySlidingTabs Layout


**activity_main.xml**

```XML
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <com.camnter.easyslidingtabs.widget.EasySlidingTabs
        android:id="@+id/easy_sliding_tabs"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:easyIndicatorColor="#ff57C1CC"
        app:easyUnderlineColor="#ffdddddd"
        app:easyTabTextColor="#ffFF4081"
        app:easySelectedTagTextColor="#ff57C1CC"
        android:paddingBottom="16dp"
        android:paddingTop="16dp" />

    <android.support.v4.view.ViewPager
        android:id="@+id/easy_vp"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1" />

</LinearLayout>

```


## FragmentPagerAdapter

```Java
public class TabsFragmentAdapter extends FragmentPagerAdapter implements EasySlidingTabs.TabsTitleInterface {

    private String[] titles;
    private List<Fragment> fragments;

    public TabsFragmentAdapter(FragmentManager fm, String[] titles, List<Fragment> fragments) {
        super(fm);
        this.fragments = fragments;
        this.titles = titles;
    }

    @Override
    public SpannableString getTabTitle(int position) {
        CharSequence title = this.getPageTitle(position);
        if (TextUtils.isEmpty(title)) return new SpannableString("");
        return new SpannableString(title);
    }

    /**
     * This method may be called by the ViewPager to obtain a title string
     * to describe the specified page. This method may return null
     * indicating no title for this page. The default implementation returns
     * null.
     *
     * @param position The position of the title requested
     * @return A title for the requested page
     */
    @Override
    public CharSequence getPageTitle(int position) {
        if (position < titles.length) {
            return titles[position];
        } else {
            return "";
        }
    }

    /**
     * Return the Fragment associated with a specified position.
     *
     * @param position position
     */
    @Override
    public Fragment getItem(int position) {
        Fragment fragment = this.fragments.get(position);
        if (fragment != null) {
            return this.fragments.get(position);
        } else {
            return null;
        }
    }

    @Override
    public int getTabDrawableBottom(int position) {
        return 0;
    }

    @Override
    public int getTabDrawableLeft(int position) {
        return 0;
    }

    @Override
    public int getTabDrawableRight(int position) {
        return 0;
    }

    @Override
    public int getTabDrawableTop(int position) {
        return 0;
    }


    /**
     * Return the number of views available.
     */
    @Override
    public int getCount() {
        return this.fragments.size();
    }

}
```

---


## EasySlidingTabs set tab background

**easyslidingtabs**  
Module：**bg_easy_sliding_tabs.xml：**

```XML
<selector xmlns:android="http://schemas.android.com/apk/res/android" android:exitFadeDuration="@android:integer/config_shortAnimTime">
    <item android:state_pressed="true" android:drawable="@color/bg_easy_sliding_tabs_pressed" />
    <item android:state_focused="true" android:drawable="@color/bg_easy_sliding_tabs_pressed" />
    <item android:drawable="@android:color/transparent" />
</selector>
```

---

## Screenshot

![readme_1](https://github.com/CaMnter/EasySlidingTabs/raw/master/screenshot/est.gif)





## License


     Copyright (C) 2015 CaMnter yuanyu.camnter@gmail.com

     Licensed under the Apache License, Version 2.0 (the "License");
     you may not use this file except in compliance with the License.
     You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

     Unless required by applicable law or agreed to in writing, software
     distributed under the License is distributed on an "AS IS" BASIS,
     WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
     See the License for the specific language governing permissions and
     limitations under the License.







