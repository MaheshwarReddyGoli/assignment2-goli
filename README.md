# assignment2-goli

# Maheshwar Reddy Goli

###### Vemullapalli

**Vemullapalli is my Hometown.** My parents live over there, **we have farms with a beautiful house.**<br>
whenever i feel stress, i love to visit my Home for relaxation.

---

# Directions for traveling from Maryville to Vemullapalli.
  1. Catch a Cab from Maryville to Kansas-city Airport.
  2. Travel by flights:
     1. First flight from kansas-city airport to chicago.
     2. Second flight from chicago to hyderabad.
  3. Come out from the airport and catch the following buses:
     1. Airport Bus to MGBS.
     2. MGBS to Vemullapalli.
  4. After dropping in vemuallapalli, take a short walk to Home.
  
* list of items to be purchased:
  * Groceries:
    * Rice
    * Vegetables
    * Snacks
    * Meat
  * Drinks:
    * Mocktails
    * Wine
    * Beer
  * Grill Set.
  * Outdoor Tent Set with Chairs.
  
**[AboutMe.md](AboutMe.md)**

---

# Here are the 4 Food/Drinks that i recommand someone to try in their lifetime.

You can find the below table for the Food Items that you should definately try:

| Food/Drink | Location | Expected Price |
| :--- | :---: | :--- |
| Biryani | Paradise, Hyderabad | INR 350 |
| Maggie | Maggie point, DLF | INR 50 |
| Ghee Idly | Tiffins point, DLF | INR 100 |
| Dosa | Ram Ki Bandi, Hyderabad | INR 100 |

---

# Quotes

> "Don't let someone be a priority when all you are to them is an option." -*Jay Shetty*</br>
> "I once read that people who study others are wise but those who study themselves are enlightened." -*Robin Sharma*

---

# Graham Scan 

> Graham's scan is a method of finding the convex hull of a finite set of points in the plane with time complexity O(n log n). It is named after Ronald Graham, who published the original algorithm in 1972. The algorithm finds all vertices of the convex hull ordered along its boundary. It uses a stack to detect and remove concavities in the boundary efficiently.

[Click here to know more](https://en.wikipedia.org/wiki/Graham_scan)

```
struct pt {
    double x, y;
};

bool cmp(pt a, pt b) {
    return a.x < b.x || (a.x == b.x && a.y < b.y);
}

bool cw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) < 0;
}

bool ccw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) > 0;
}

void convex_hull(vector<pt>& a) {
    if (a.size() == 1)
        return;

    sort(a.begin(), a.end(), &cmp);
    pt p1 = a[0], p2 = a.back();
    vector<pt> up, down;
    up.push_back(p1);
    down.push_back(p1);
    for (int i = 1; i < (int)a.size(); i++) {
        if (i == a.size() - 1 || cw(p1, a[i], p2)) {
            while (up.size() >= 2 && !cw(up[up.size()-2], up[up.size()-1], a[i]))
                up.pop_back();
            up.push_back(a[i]);
        }
        if (i == a.size() - 1 || ccw(p1, a[i], p2)) {
            while(down.size() >= 2 && !ccw(down[down.size()-2], down[down.size()-1], a[i]))
                down.pop_back();
            down.push_back(a[i]);
        }
    }

    a.clear();
    for (int i = 0; i < (int)up.size(); i++)
        a.push_back(up[i]);
    for (int i = down.size() - 2; i > 0; i--)
        a.push_back(down[i]);
}
```

[Code Source](https://cp-algorithms.com/geometry/grahams-scan-convex-hull.html)