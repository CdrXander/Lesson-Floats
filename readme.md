You've heard of "clearing floats", but do you really understand it? The whole problem is that floated objects do not add to the height of the object the reside in properly. As you can see below, these divs with the class "floated_box" are within the div "main_container", yet on the page they are outside that container div.

All we need to do is clear the float, and this entire problem goes away. Put this empty div AFTER your last floated object:
<div style="clear: both;"></div>

Float Properties- There are four valid values for the float property. Left and Right float elements those directions respectively. None (the default) ensures the element will not float and Inherit which will assume the float value from that elements parent element.


Clearing Floats- Float's sister property is clear. An element that has the clear property set on it will not move up adjacent to the float like the float desires, but will move itself down past the float. Clear has four valid values as well. Both is most commonly used, which clears floats coming from either direction. Left and Right can be used to only clear the float from one direction respectively. None is the default, which is typically unnecessary unless removing a clear value from a cascade
Clearing only the left or right float, while less commonly seen in the wild, definitely has its uses.


Float Breaking- One of the more bewildering things about working with floats is how they can affect the element that contains them (their "parent" element). If this parent element contained nothing but floated elements, the height of it would literally collapse to nothing. This isn't always obvious if the parent doesn't contain any visually noticeable background, but it is important to be aware of. Collapsing almost always needs to be dealt with to prevent strange layout and cross-browser problems. We fix it by clearing the float after the floated elements in the container but before the close of the container.

Techniques to Clear Floats- If you are in a situation where you always know what the succeeding element is going to be, you can apply the clear: both; value to that element and go about your business. This is ideal as it requires no fancy hacks and no additional elements making it perfectly semantic. Of course things don't typically work out that way and we need to have more float-clearing tools in our toolbox.

1. The Empty Div Method is, quite literally, an empty div. <div style="clear: both;"></div>. Sometimes you'll see a <br> element or some other random element used, but div is the most common because it has no browser default styling, doesn't have any special function, and is unlikely to be generically styled with CSS.

2. The Overflow Method relies on setting the overflow CSS property on a parent element. If this property is set to auto or hidden on the parent element, the parent will expand to contain the floats, effectively clearing it for succeeding elements. This method can be beautifully semantic as it may not require an additional elements. However if you find yourself adding a new div just to apply this, it is equally as non-semantic as the empty div method and less adaptable. Also bear in mind that the overflow property isn't specifically for clearing floats. Be careful not to hide content or trigger unwanted scrollbars.

3. The Easy Clearing Method uses a clever CSS pseudo selector (:after) to clear floats. Rather than setting the overflow on the parent, you apply an additional class like "clearfix" to it. Then apply this CSS:

.clearfix:after {
   content: ".";
   visibility: hidden;
   display: block;
   height: 0;
   clear: both;
}
