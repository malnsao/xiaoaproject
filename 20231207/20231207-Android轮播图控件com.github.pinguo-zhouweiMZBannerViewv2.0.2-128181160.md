build.gradle 配置：

>
>     dependencies {
>  
>     compile 'com.github.pinguo-zhouwei:MZBannerView:v2.0.2'
>  
>      }
>  

xml布局：

>
>     <com.zhouwei.mzbanner.MZBannerView
>         android:id="@+id/banner"
>         android:layout_width="match_parent"
>         android:layout_height="140dp"
>         android:layout_marginLeft="20dp"
>         android:layout_marginRight="20dp"
>         android:layout_marginTop="20dp"
>         android:layout_marginBottom="5dp"
>         app:canLoop="true"
>         app:indicatorAlign="center"
>         app:indicatorPaddingLeft="10dp"
>         app:open_mz_mode="false"
>         />

banner图片布局：

>
>     <com.facebook.drawee.view.SimpleDraweeView
>         android:id="@+id/bannerImage"
>         android:layout_width="match_parent"
>         android:layout_height="130dp"
>         android:layout_gravity="center"
>         android:adjustViewBounds="true"
>         fresco:roundedCornerRadius="5dp" />
>  
>  

activity使用：

>
>     //获取控件
>     MZBannerView mMZBanner = (MZBannerView)
> rootView.findViewById(R.id.banner);
>
> //添加图片地址
>  
>  
>     mImgList.add("imgPath");
>     mImgList.add("imgPath");t
>
> //图片显示
>  
>  
>     mMZBanner.setPages(mImgList, new
> MZHolderCreator<IndexFragment.BannerViewHolder>() {
>         @Override
>         public IndexFragment.BannerViewHolder createViewHolder() {
>             return new IndexFragment.BannerViewHolder();
>         }
>     });
>  
>  
>     public static class BannerViewHolder implements MZViewHolder<String> {
>         private SimpleDraweeView mImageView;
>  
>         @Override
>         public View createView(Context context) {
>             // 返回页面布局
>             View view =
> LayoutInflater.from(context).inflate(R.layout.banner_item, null);
>             mImageView = (SimpleDraweeView)
> view.findViewById(R.id.bannerImage);
>             return view;
>         }
>  
>         @Override
>         public void onBind(Context context, int position, String data) {
>             Uri uIconuri = Uri.parse(data);
>             FrescoUtils.initDraweeController(mImageView, uIconuri);
>  
>         }
>     }

效果图：

![](./res/842b8f23b34845cfb2c355c0fb3d198a.jpeg)

