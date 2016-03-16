# Swipes View Library (Android)
SwipesView displays **views (or cards) to be swiped** in all **directions of your choice** and also allows you to **programatically swipe** (with a button or a command).

![swipes](https://raw.github.com/jacobmoncur/QuiltViewLibrary/master/nexus7.png "SwipesView") ![swipes](https://raw.github.com/jacobmoncur/QuiltViewLibrary/master/nexus7_mayer.png "SwipesView")

Setup
-----

The SwipesView can be defined in XML:

    <?xml version="1.0" encoding="utf-8"?>
	<us.the.mac.swipes.SwipesView 
	    xmlns:android="http://schemas.android.com/apk/res/android"
	    xmlns:swipes="http://schemas.android.com/apk/res-auto"
	    android:id="@+id/container"
	    android:layout_width="match_parent"
	    android:layout_height="match_parent"
	    android:background="#40aeaeae"
	    swipes:directions="right|down"
	    swipes:swipe_rotation="15.5" />
    
Or programmatically
    
    //The array defines which directions the SwipesView will swipe to
    Directions directions[] = new Directions[] { Directions.RIGHT, Directions.DOWN };
    
    SwipesView swipesView = new SwipesView(context); //(SwipesView) findViewById(R.id.swipes);
	swipesView.setAllowedDirections(directions); //setAllowedDirections(Directions.RIGHT, Directions.DOWN);
        
Passing Data
---------------

Data must be passed to the SwipesView inside of the SwipesAdapter:

	swipesView.setAdapter(new BasicExampleSwipesAdapter(this, R.layout.card_item));
	
A basic example of a SwipesAdadpter subclass would look as follows:
	
	class BasicExampleSwipesAdapter extends SwipesAdapter<Integer> {
		ArrayList<Integer> mInts = new ArrayList<Integer>(Arrays.asList(new Integer[]{
			1, 11, 111
		}));
		public BasicExampleSwipesAdapter(Context context, int resource) {
			super(context, resource);
		}
		@Override public View getView (int position, View convertView, ViewGroup parent) {
			View inflatedResource = super.getView(position, convertView, parent);
			TextView card_text = (TextView) inflatedResource.findViewById(R.id.card_text);
			
			String integer = getItem(position);
			card_text.setText(integer);
			
			return inflatedResource;
		}
		@Override public Integer getItem(int position) { return mInts.get(position); }
		@Override public void removeItem(int position) { mInts.remove(position); }
		@Override public int getCount() { return mInts.size(); }
	}


Automating Swipes
---------------

The SwipesView can supercede the finger swipe programatically, ideally through a button click or command:

	Button swipeLeftButton = new Button(context);
	swipeLeftButton.setOnClickListener(new View.OnClickListener() {
		@Override public void onClick(View v) { swipesView.onSwipeLeft(); }
	});
	
	Button swipeRightButton = new Button(context);
	swipeRightButton.setOnClickListener(new View.OnClickListener() {
		@Override public void onClick(View v) { swipesView.onSwipeRight(); }
	});
	
	Button swipeUpButton = new Button(context);
	swipeUpButton.setOnClickListener(new View.OnClickListener() {
		@Override public void onClick(View v) { swipesView.onSwipeUp(); }
	});
	
	Button swipeDownButton = new Button(context);
	swipeDownButton.setOnClickListener(new View.OnClickListener() {
		@Override public void onClick(View v) { swipesView.onSwipeDown(); }
	});
	
Further Reading
---------------

See the [Javadocs](https://pages.github.com/Operators/swipes-view-android) for more on the SwipesView, SwipesAdapter functions.

See the [MAC Guide](#) for detailed examples of how to use the SwipesView.

See the [Android Javadocs](#) for more on AdapterView, for a peek into the SwipesView origins.

See the [Android Javadocs](#) for more on BaseAdapter, to see how the SwipesAdapter started.

	
LICENSE
===============
The MIT License (MIT)
Copyright (c) 2016 Christopher

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
