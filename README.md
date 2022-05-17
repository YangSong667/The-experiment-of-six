#include<stdio.h>
typedef struct country
{
	char name[100];
	int gold;
	int silver;
	int bronze;
	int total;
}country;
void sort(country a[], int n)
{
	for (int i = 0; i<n; i++)
	{
		for (int j = 0; j<n - 1; j++)
		{
			if (a[j].gold>a[j + 1].gold)
			{
				country t = a[j];
				a[j] = a[j + 1];
				a[j + 1] = t;
			}
		}
	}
}
int main()
{
	FILE*infp = fopen("D:\\金牌排序.txt", "r");
	if (infp == NULL)
	{
		printf("Error\n");
		return 0;
	}
	country c[8];
	int i = 0;
	while (fscanf(infp, "%s %d %d %d %d", c[i].name, &c[i].gold, &c[i].silver, &c[i].bronze, &c[i].total) != EOF)
	{
		i++;
	}
	fclose(infp);
	sort(c, 8);
	for (i = 0; i<8; i++)
	{
		printf("%s\t%d\t%d\t%d\t%d\n", c[i].name, c[i].gold, c[i].silver, c[i].bronze, c[i].total);
	}
	FILE*outfp = fopen("D:\\金牌排序_sorted.txt", "w");
	for (i = 0; i<8; i++)
	{
		fprintf(outfp, "%s\t%d\t%d\t%d\t%d\n", c[i].name, c[i].gold, c[i].silver, c[i].bronze, c[i].total);
	}
	fclose(outfp);
	return 0;
}
