# c_blog

Table of Contents:
- [Designated Initializers](#designated-initializers)

## Designated Initializers

```C
// C program to demonstrate designated
// initializers with structures
#include <stdio.h>
struct Point
{
	int x, y, z;
};

int main()
{
	
	// Examples of initialization using
	// designated initialization
	struct Point p1 = {.y = 0, .z = 1, .x = 2};
	struct Point p2 = {.x = 20};
	
	printf("x = %d, y = %d, z = %d\n",
		p1.x, p1.y, p1.z);
		
	printf("x = %d", p2.x);
	
	return 0;
}
```

Designated Initializers with struct arrays

```C
// C program to demonstrate designated initializers
// with structures and arrays combined
#include <stdio.h>
void main(void)
{
	struct point { int x, y; };
	struct point pts[5] = { [2].y = 5, [2].x = 6, [0].x = 2 };
	int i;
	for (i = 0; i < 5; i++)
		printf("%d %d\n", pts[i].x ,pts[i].y);
}
```

