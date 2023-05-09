# c_blog

Table of Contents:
- [Cool C features](#cool-c-features)

## Cool C features

Designated Initializers

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

Sample
