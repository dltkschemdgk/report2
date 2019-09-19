#include<stdio.h>
#include<stdlib.h>
int add(int a, int b) {
 return a + b;
}
int main() {
 int a, b;
 FILE* fp = fopen("my.txt", "r");
 if (fp == NULL) { 
  puts("File not found!!");
  exit(0); 
 }
 fscanf(fp, "%d%d", &a, &b);
 fclose(fp);
 printf("%d\n", add(a, b));
}
-----
예상되는 문제입니다 -구조체를 선언과 동시에 초기화 하여 18 jcshim 을 출력하시오-
#include<stdio.h>
struct user{
	int age;
	char n[80];
} me = {18, "jcshim"};
void main(){
	printf("%d %s\n", me.age, me.n);
}
