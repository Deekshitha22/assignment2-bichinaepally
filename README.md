# assignment2-bichinaepally
# Deekshitha Bichinaepally
###### My favorite place is Hyderabad
Hyderabad is a place where all sort of people live irrespective of the **religion**. I was born and bought up in hyderabad. It's a place where you get every essential thing and hyderabad is also famous for **biryani**. 

***

# favorite place
 
 1. Go to kansas city(airport) from maryville
    1. Self check in at airport
    2. collect boarding pass.
    3. security check up
    4. enter flight
    5. fly
 2. kansas city airport to rajeev gandhi international airport through flight.
 3.  Reach Rajeev gandhi international airport which is located in hyderabad.
 4. My favorite destination hyderabad has arrived.
 5. Go to home in cab.
 * bring games
   *Go to sports shop 
   *Buy games  
      *hockey
      *cricket bat and ball
   *Buy snacks
   *go back to favourite place


[About me](https://github.com/Deekshitha22/assignment2-bichinaepally/blob/main/AboutMe.md)

***

# favorite foods
I like south Indian food, below are the food items
|  Food items               | location       |  cost    |
| --------------------------| -------------- | ---------|
| idli                      |  Hyderabad     | 60       |
| dosa                      |  Hyderabad     | 100      |
| vada                      |  Hyderabad     | 50       |
| sambar                    |  Hyderabad     | 30       |

***

# favourite quotes
> Life is a journey, not a destination. - *Ralph waldo emerson*.

> Not all who wander are lost. - *J.R.R Tolkien*.

***

# code fencing
> **Bentley–Ottmann algorithm**  In computational geometry, the Bentley–Ottmann algorithm is a sweep line algorithm for listing all crossings in a set of line segments, i.e. it finds the intersection points (or, simply, intersections) of line segments. It extends the Shamos–Hoey algorithm,[1] a similar previous algorithm for testing whether or not a set of line segments has any crossings. For an input consisting of {\displaystyle n}n line segments with {\displaystyle k}k crossings (or intersections), the Bentley–Ottmann algorithm takes time {\displaystyle {\mathcal {O}}((n+k)\log n)}{\displaystyle {\mathcal {O}}((n+k)\log n)}. In cases where {\displaystyle k={\mathcal {o}}\left({\frac {n^{2}}{\log n}}\right)}{\displaystyle k={\mathcal {o}}\left({\frac {n^{2}}{\log n}}\right)}, this is an improvement on a naïve algorithm that tests every pair of segments, which takes {\displaystyle \Theta (n^{2})}\Theta (n^{2}).

The algorithm was initially developed by Jon Bentley and Thomas Ottmann (1979); it is described in more detail in the textbooks Preparata & Shamos (1985), O'Rourke (1998), and de Berg et al. (2000). Although asymptotically faster algorithms are now known by Chazelle & Edelsbrunner (1992) and Balaban (1995), the Bentley–Ottmann algorithm remains a practical choice due to its simplicity and low memory requirements[citation needed].

[link to source](https://en.wikipedia.org/wiki/Bentley%E2%80%93Ottmann_algorithm)

Sample code
```
class GFG
{
 
static class Point
{
    int x;
    int y;
 
        public Point(int x, int y)
        {
            this.x = x;
            this.y = y;
        }
     
};
 
// Given three colinear points p, q, r, the function checks if
// point q lies on line segment 'pr'
static boolean onSegment(Point p, Point q, Point r)
{
    if (q.x <= Math.max(p.x, r.x) && q.x >= Math.min(p.x, r.x) &&
        q.y <= Math.max(p.y, r.y) && q.y >= Math.min(p.y, r.y))
    return true;
 
    return false;
}
 
// To find orientation of ordered triplet (p, q, r).
// The function returns following values
// 0 --> p, q and r are colinear
// 1 --> Clockwise
// 2 --> Counterclockwise
static int orientation(Point p, Point q, Point r)
{
    // See https://www.geeksforgeeks.org/orientation-3-ordered-points/
    // for details of below formula.
    int val = (q.y - p.y) * (r.x - q.x) -
            (q.x - p.x) * (r.y - q.y);
 
    if (val == 0) return 0; // colinear
 
    return (val > 0)? 1: 2; // clock or counterclock wise
}
 
// The main function that returns true if line segment 'p1q1'
// and 'p2q2' intersect.
static boolean doIntersect(Point p1, Point q1, Point p2, Point q2)
{
    // Find the four orientations needed for general and
    // special cases
    int o1 = orientation(p1, q1, p2);
    int o2 = orientation(p1, q1, q2);
    int o3 = orientation(p2, q2, p1);
    int o4 = orientation(p2, q2, q1);
 
    // General case
    if (o1 != o2 && o3 != o4)
        return true;
 
    // Special Cases
    // p1, q1 and p2 are colinear and p2 lies on segment p1q1
    if (o1 == 0 && onSegment(p1, p2, q1)) return true;
 
    // p1, q1 and q2 are colinear and q2 lies on segment p1q1
    if (o2 == 0 && onSegment(p1, q2, q1)) return true;
 
    // p2, q2 and p1 are colinear and p1 lies on segment p2q2
    if (o3 == 0 && onSegment(p2, p1, q2)) return true;
 
    // p2, q2 and q1 are colinear and q1 lies on segment p2q2
    if (o4 == 0 && onSegment(p2, q1, q2)) return true;
 
    return false; // Doesn't fall in any of the above cases
}
 
// Driver code
public static void main(String[] args)
{
    Point p1 = new Point(1, 1);
    Point q1 = new Point(10, 1);
    Point p2 = new Point(1, 2);
    Point q2 = new Point(10, 2);
 
    if(doIntersect(p1, q1, p2, q2))
        System.out.println("Yes");
    else
        System.out.println("No");
 
    p1 = new Point(10, 1); q1 = new Point(0, 10);
    p2 = new Point(0, 0); q2 = new Point(10, 10);
    if(doIntersect(p1, q1, p2, q2))
            System.out.println("Yes");
    else
        System.out.println("No");
 
    p1 = new Point(-5, -5); q1 = new Point(0, 0);
    p2 = new Point(1, 1); q2 = new Point(10, 10);;
    if(doIntersect(p1, q1, p2, q2))
        System.out.println("Yes");
    else
        System.out.println("No");
}
}
```

[source](https://www.geeksforgeeks.org/check-if-two-given-line-segments-intersect/)

