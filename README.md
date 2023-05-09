# c_blog

Table of Contents:
- [Designated Initializers](#designated-initializers)
- [Compound Literals](#compound-literals)
- strcat, strcpy, strlen
- memmove, realloc, calloc, memcpy
- string
- typedef (pointer star location)
- function pointer (callbacks)
- struct composition (inheritance)
- union (multiple inheritance)

## Designated Initializers

In ISO C99 you can give the elements in random order, specifying the array indices or structure field names they apply to

```C
#include <stdio.h>
typedef struct Point {
  int x;
  int y;
  int z;
} Point;

int main(int argc, char* argv[]) {
  struct Point p1 = {.y = 0, .z = 1, .x = 2};
  struct Point p2 = {.x = 20};
	
  printf("x = %d, y = %d, z = %d\n", p1.x, p1.y, p1.z);
  printf("x = %d", p2.x);
	
  return 0;
}
```

Designated Initializers with struct arrays

```C
#include <stdio.h>

typedef struct Point {
  int x;
  int y;
} Point;

int main(int argc, char* argv[]) {
  Point pts[5] = { [2].y = 5, [2].x = 6, [0].x = 2 };
  for (int i = 0; i < 5; i++) {
    printf("%d %d\n", pts[i].x ,pts[i].y);
  }
}
```

## Compound Literals

Constructs an unnamed object of specified type (which may be struct, union, or even array type) in-place

```C
#include <stdio.h>
 
void drawline1(struct point from, struct point to) {
    printf("drawline1: `from` @ %p {%.2f, %.2f}, `to` @ %p {%.2f, %.2f}\n",
        (void*)&from, from.x, from.y, (void*)&to, to.x, to.y);
}
 
void drawline2(struct point *from, struct point *to) {
    printf("drawline2: `from` @ %p {%.2f, %.2f}, `to` @ %p {%.2f, %.2f}\n",
        (void*)from, from->x, from->y, (void*)to, to->x, to->y);
}

int main(int argc, char* argv[]) {
    drawline1(
        (struct point){.x=1, .y=1},  // creates two structs with block scope and
        (struct point){.x=3, .y=4}); // calls drawline1, passing them by value
    drawline2(
        &(struct point){.x=1, .y=1},  // creates two structs with block scope and
        &(struct point){.x=3, .y=4}); // calls drawline2, passing their addresses
}
 
```

