# first-project
sudo

    how to use ConvenientBanner

    import: build.gradle---->compile 'com.bigkoo:convenientbanner:2.0.5'
    xml:xxx.xml---->

                            <com.bigkoo.convenientbanner.ConvenientBanner xmlns:app="http://schemas.android.com/apk/res-auto"
                            android:id="@+id/convenientBanner"
                            android:layout_width="match_parent"
                            android:layout_height="264dp"
                            android:background="#ffffff"
                            app:canLoop="true" />
    java:xxx.java---->

        ArrayList<Integer> localImages = new ArrayList<Integer>();
        localImages.add(R.drawable.a);
        localImages.add(R.drawable.b);
        localImages.add(R.drawable.c);
        localImages.add(R.drawable.d);
        localImages.add(R.drawable.e);
        
        ConvenientBanner convenientBanner = (ConvenientBanner)findViewById(R.id.convenientBanner);
        convenientBanner.setPages(
                new CBViewHolderCreator<LocalImageHolderView>() {
                    @Override
                    public LocalImageHolderView createHolder() {
                        return new LocalImageHolderView();
                    }
                }, localImages)
                //设置两个点图片作为翻页指示器，不设置则没有指示器，可以根据自己需求自行配合自己的指示器,不需要圆点指示器可用不设
                .setPageIndicator(new int[]{R.drawable.mm1, R.drawable.mm2}).setOnItemClickListener(this);
                
                convenientBanner.startTurning(3000);
                convenientBanner.stopTurning();
                
                
        public class LocalImageHolderView implements Holder<Integer> {
        private ImageView imageView;

        @Override
        public View createView(Context context) {
            imageView = new ImageView(context);
            imageView.setScaleType(ImageView.ScaleType.FIT_XY);
            return imageView;
        }

        @Override
        public void UpdateUI(Context context, final int position, Integer data) {
            imageView.setImageResource(data);
        }
    }
        
        


