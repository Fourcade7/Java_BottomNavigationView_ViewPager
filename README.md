# Java_BottomNavigationView_ViewPager
BottomNavigationView Swipe

![image](https://user-images.githubusercontent.com/60017090/137576121-ea35dabb-b17c-4608-b707-51353a1a2c94.png)

    public class MyPager extends FragmentStatePagerAdapter {

    public MyPager(@NonNull FragmentManager fm) {
        super(fm);
    }

    @NonNull
    @Override
    public Fragment getItem(int position) {

        switch (position){
            case 0:
                return new BlankFragment();
            case 1:
                return new BlankFragment2();
            case 2:
                return new BlankFragment3();
        }
        return null;
    }

    @Override
    public int getCount() {
        return 3;
      }
    }
