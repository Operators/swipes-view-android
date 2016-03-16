# Swipes View Library (Android)
[SwipesView](http://operators.github.io/swipes-view-android/com/operators/swipes/SwipesView.html) displays **views (or cards) to be swiped** in all **directions of your choice** and also allows you to **programatically swipe** (with a button or a command).

![swipes](https://raw.githubusercontent.com/Operators/swipes-view-android/master/d2ucKOT49Hchristopher03162016012902.gif "SwipesView") ![swipes](https://raw.githubusercontent.com/Operators/swipes-view-android/master/d2ucKOT49Hchristopher03162016013504.gif "SwipesView")

Setup
-----

The [SwipesView](http://operators.github.io/swipes-view-android/com/operators/swipes/SwipesView.html) can be defined programmatically in Java:
    
    //The array defines which directions the SwipesView will swipe to
    Directions directions[] = new Directions[] { Directions.LEFT, Directions.RIGHT };
    
    SwipesView swipesView = new SwipesView(context); //(SwipesView) findViewById(R.id.swipes);
	swipesView.setAllowedDirections(directions); //setAllowedDirections(Directions.RIGHT, Directions.DOWN);
        
    
Or in an Android XML Layout:

    <?xml version="1.0" encoding="utf-8"?>
	<com.operators.swipes.SwipesView 
	    xmlns:android="http://schemas.android.com/apk/res/android"
	    xmlns:swipes="http://schemas.android.com/apk/res-auto"
	    android:id="@+id/container"
	    android:layout_width="match_parent"
	    android:layout_height="match_parent"
	    android:background="#40aeaeae"
	    swipes:directions="right|down"
	    swipes:swipe_rotation="15.5" />
	    
Passing Data
---------------

Data must be passed to the [SwipesView](http://operators.github.io/swipes-view-android/com/operators/swipes/SwipesView.html) from a [SwipesAdapter](http://operators.github.io/swipes-view-android/com/operators/swipes/SwipesAdapter.html) subclass:

	swipesView.setAdapter(new BasicExampleSwipesAdapter(this, R.layout.card_item));
	
A basic example of a [SwipesAdapter](http://operators.github.io/swipes-view-android/com/operators/swipes/SwipesAdapter.html) subclass would look as follows:
	
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

The [SwipesView](http://operators.github.io/swipes-view-android/com/operators/swipes/SwipesView.html) can swipe programatically as well, ideally through a button click (or some other action):

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

See the [Javadocs](http://operators.github.io/swipes-view-android) for more on the [SwipesView](http://operators.github.io/swipes-view-android/com/operators/swipes/SwipesView.html), or [SwipesAdapter](http://operators.github.io/swipes-view-android/com/operators/swipes/SwipesAdapter.html) functions.

See the [MAC Guides](#) for detailed examples of how to use the [SwipesView](http://operators.github.io/swipes-view-android/com/operators/swipes/SwipesView.html).
* Like with a [Basic Example](#)
* Interacting with other [View Components](#)
* Or with [SwipesViewListeners](#).

See the [Android Javadocs](http://developer.android.com/reference/android/widget/AdapterView.html) for more on [AdapterView](https://github.com/android/platform_frameworks_base/blob/master/core/java/android/widget/AdapterView.java), for a peek into the SwipesView origins.

See the [Android Javadocs](http://developer.android.com/reference/android/widget/BaseAdapter.html) for more on [BaseAdapter](https://github.com/android/platform_frameworks_base/blob/7de7e0b0dd61acba813dec3a07d29f1d62026470/core/java/android/widget/BaseAdapter.java), to see how the SwipesAdapter started.

	
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
