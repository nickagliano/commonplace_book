# Quadtree

I want to do a bit of an exploration, and "discover" what a quadtree is and why you would use it.

If you don't want to do that, you can click below the spoiler warning below and get a sneak preview at the definition of a quadtree.

<details>
  <summary>
    Spoiler! (definition of a quadtree)
  </summary>

> A quadtree is a tree data structure used for recursive partitioning of a 2D space into four quadrants.

</details>

Okay, so let's explore the quadtree through the same lens that I was first introduced -- an [interview question](https://www.youtube.com/watch?v=RA11Zpggtp4).

## K Nearest Restaurants

Here is the question:

> Given a list of 100 million (`n`) restaurants, write a function that takes a user's location and returns the 10 (`k`) nearest restaurants.

So, the first thing you might do is clarify the question -- what sort of data are we really looking at here?

Well, we're talking about geographic coordinates -- longtitude and latitude.

So, the pseudocode might look like:

```
struct Location:
  x: f64
  y: f64

User:
  id: i32
  ... other fields ...
  loc: Location

Restaurant:
  id: i32
  ... other fields ...
  loc: Location
```

First let's look at some naïve solutions. These will work, pretty well in some scenarios, but they're not the optimal.

First way you could solve this--you could sort.

To do this, you will need to find the euclidean distance between the user and each of the 100 million restaurants. You could call that the restaurants "value. Then sort by the restaraunts "value" and grab the 10 smallest values.

This takes `O(n log n)`.

An improved solution:

`k` should be rather small, so it would be preferrable to do something like, a left to right scan, with a priority queue of size `k`, then the big O time would be: `O(n log k)`.

The interviewee then notes the memory factor (which, man, is such a great thing to do in an interview).

He notes that the brute sort has an O(n) memory footprint, and the left to right scan with priority queue has a O(k) memory footprint.

And he even notes the priority queue could be "streamed" if it didn't fit in memory.

But he estimated that the memory footprint would be ~100 MB, and noted that 100 MB should be plenty enough on "most devices".

The interviewer gives his kudos. This solution was especially impressive given the fact that he came up with it in about 5 minutes of conversation. But he notes:

> If you were in Tokyo, do you think you would even consider the restaurants in London?

to be continued... (right around 7:00 minutes in the video)
