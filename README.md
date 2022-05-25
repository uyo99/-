#include<stdio.h>

void print(int totalcredit, double totalpoint);

#define NUMOFLECTURE 8

char *lecture[NUMOFLECTURE][2] = {{"교선", "정보보호개론"},
{"교선" , "네트워크 일반"},
{"교선" , "기초운영체제 실습"},
{"전선" , "정보통신개론"},
{"전선" , "컴퓨터 운영체제"},
{"전필" , "네트워크 구축"},
{"전필" , "c언어 실습"},
{"전필" , "컴퓨터 구조"}};


char *GRADE[] = {"F","D0","D+","C0","C+","B0","C+","A0","A+"};

double GRADEPOINT[] = {0.0, 1.0, 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5};

int point[NUMOFLECTURE][2];
int grade[NUMOFLECTURE];

int main(void)
{
double totalpoint = 0.0;
int totalcredit = 0;
int i=0;

printf("*************************************************************\n");
printf("\tA+ : 95 ~ 100, A0 : 90 ~ 94 \n");
printf("\tB+ : 85 ~  89, B0 : 80 ~ 84 \n");
printf("\tC+ : 75 ~  79, C0 : 70 ~ 74 \n");
printf("\tD+ : 65 ~  69, D0 : 60 ~ 64 \n");
printf("\tF  : 59이하 ");
printf("\n*************************************************************\n");

printf("입력 예>>\n");
printf("%6s%30s >>", lecture[0][0], lecture[0][1]);
printf(">> 2(학점) 96(점수)\n\n");

printf("지금부터 입력하세요.>>\n");

for(i=0; i<NUMOFLECTURE; i++)
{
printf("%6s%30s >> ", lecture[i][0], lecture[i][1]);
scanf("%d %d", &point[i][0], &point[i][1]);
grade[i] = point[i][1] / 5;
totalpoint += point[i][0] * GRADEPOINT[grade[i]-11];
totalcredit += point[i][0];
}

print(totalcredit, totalpoint);

return 0;
}

void print(int totalcredit, double totalpoint)
{
int i;

printf("\n*************************************************************\n");
printf("%7s%18s%17s%18s\n", "구분", "과 목 명", "학점", "성적");
printf("\n*************************************************************\n");

for(i=0; i<NUMOFLECTURE; i++)
{
printf("%7s%23s%12d%16s\n", lecture[i][0], lecture[i][1],point[i][0],GRADE[grade[i]-11]);
}

printf("\n*************************************************************\n");
printf("%7s%18s%17s%18s\n", "학점계", "평 점 계", "평점평균", "백분율환산");
printf("\n*************************************************************\n");

printf("%7d%17.1f%14.2f/4.5%17.1f\n", totalcredit, totalpoint,
(totalpoint/totalcredit), 100*(totalpoint/totalcredit)/4.5);
printf("\n*************************************************************\n");
}
