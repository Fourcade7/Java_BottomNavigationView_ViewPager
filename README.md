# Java_BottomNavigationView_ViewPager
BottomNavigationView Swipe

![image](https://user-images.githubusercontent.com/60017090/137576121-ea35dabb-b17c-4608-b707-51353a1a2c94.png)

//MyPager.class

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

//MainActivity

    public class MainActivity extends AppCompatActivity {

    BottomNavigationView bottomNavigationView;
    ViewPager viewPager;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        bottomNavigationView = findViewById(R.id.bottomnavigationview);
        viewPager = findViewById(R.id.viewpager1);

        MyPager myPager = new MyPager(getSupportFragmentManager());
        viewPager.setAdapter(myPager);

        bottomNavigationView.setOnNavigationItemSelectedListener(new BottomNavigationView.OnNavigationItemSelectedListener() {
            @Override
            public boolean onNavigationItemSelected(@NonNull MenuItem item) {

                switch (item.getItemId()) {

                    case R.id.item1:
                        viewPager.setCurrentItem(0);
                        break;
                    case R.id.item2:
                        viewPager.setCurrentItem(1);
                        break;
                    case R.id.item3:
                        viewPager.setCurrentItem(2);
                        break;
                }


                return true;
            }
        });

        viewPager.addOnPageChangeListener(new ViewPager.OnPageChangeListener() {
            @Override
            public void onPageScrolled(int position, float positionOffset, int positionOffsetPixels) {

            }

            @Override
            public void onPageSelected(int position) {
                switch (position) {

                    case 0:
                        bottomNavigationView.getMenu().findItem(R.id.item1).setChecked(true);
                        break;
                    case 1:
                        bottomNavigationView.getMenu().findItem(R.id.item2).setChecked(true);
                        break;
                    case 2:
                        bottomNavigationView.getMenu().findItem(R.id.item3).setChecked(true);
                        break;
                }
            }

            @Override
            public void onPageScrollStateChanged(int state) {

            }
        });
     }
    }


