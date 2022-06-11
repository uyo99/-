#include<stdio.h>
#include <string.h>      

void main() {
	char name[10] = '\0'; //이름
	char grade = '\0';    //학점 등급 grade

	int scoreINF = 0; //정보보안 INFOSEC
	int scoreSGL = 0; //정보통신 signal
	int scoreNET = 0; //네트워크 일반 network
	int scoreCOM = 0; //컴퓨터 구조 computer
	int scoreCOS = 0; //컴퓨터 운영체계 computer OS?
	int scoreNEP = 0; //네트워크 구축 실습 network Practice
	int scoreCLG = 0; //C언어 C language?
	int scoreBOS = 0; //기초 운영체제 실 습



	int scoreTotal = 0;         // 총점
	float scoreAverage = 0.0F;  // 평균

	char menuChoice = '\0';     // 메뉴 선택

	char temp[256] = "\0"; //임력값 임시저장
	int len = 0;           // 입력값 길이



	do
	{
		// 메뉴 출력
		printf("*** 성적관리 프로그램 ***\n");
		printf("\n");
		printf("1. 학생 성적 입력\n");
		printf("2. 성적 확인\n");
		printf("\n");
		printf("Q. 프로그램 종료\n");
		printf("\n");
		printf("번호를 입력하세요 : ");


		// 메뉴 선택
		menuChoice = getchar();

		switch (menuChoice)
		{
		case '1':
		{


			//학생 입력 부분

			do
			{
				printf("\n*************************************************************\n");
				printf("이름 입력 :");
				scanf_s("%s", temp, sizeof(temp));
				len = strlen(temp) + 1;

				if (len > sizeof(name))
					printf("너무 긴 이름을 입력하셨습니다.\n");
				else

					strcpy_s(name, sizeof(name), temp);
			} while (len > sizeof(name));

			printf("정보보안개론 입력 :");
			scanf_s("%d", &scoreINF);

			printf("정보통신개론 입력 :");
			scanf_s("%d", &scoreSGL);

			printf("네트워크 일반 입력 :");
			scanf_s("%d", &scoreNET);

			printf("컴퓨터 구조 입력 :");
			scanf_s("%d", &scoreCOM);

			printf("컴퓨터 운영체계 입력 :");
			scanf_s("%d", &scoreCOS);

			printf("네트워크 구축 실습 입력 :");
			scanf_s("%d", &scoreNEP);

			printf("C언어 입력 :");
			scanf_s("%d", &scoreCLG);

			printf("기초 운영체제 실습 입력 :");
			scanf_s("%d", &scoreBOS);
			printf("\n*************************************************************\n");

			getchar();

		}

		break;



		case '2':
		{


			// 총점 계산
			scoreTotal = scoreINF + scoreSGL + scoreNET + scoreCOM + scoreCOS + scoreNEP + scoreCLG + scoreBOS;

			// 평균 계산
			//scoreAverage = (float) scoreTotal / 8;

			// 소수점 아래 값 손실
			scoreAverage = scoreTotal / 8;



			// 등급 구하기
			if (scoreAverage >= 95)
				grade = 'A+';
			else if (scoreAverage >= 90)
				grade = 'A';
			else if (scoreAverage >= 85)
				grade = 'B+';
			else if (scoreAverage >= 80)
				grade = 'B';
			else if (scoreAverage >= 75)
				grade = 'C+';
			else if (scoreAverage >= 70)
				grade = 'C';
			else if (scoreAverage >= 65)
				grade = 'D+';
			else if (scoreAverage >= 60)
				grade = 'D';
			else
				grade = 'F';



			// 화면 출력
			printf("\n*************************************************************\n");
			printf("%s의 성적\n", name);
			printf("총점 : %d\n평균 : %f\n\n", scoreTotal, scoreAverage);
			printf("등급 : %c\n", grade);
			printf("보안  점수 : %d\n\n", scoreINF);
			printf("통신  점수 : %d\n\n", scoreSGL);
			printf("네트  점수 : %d\n\n", scoreNET);
			printf("컴구  점수 : %d\n\n", scoreCOM);
			printf("컴운  점수 : %d\n\n", scoreCOS);
			printf("네구  점수 : %d\n\n", scoreNEP);
			printf("C언어 점수 : %d\n\n", scoreCLG);
			printf("기운  점수 : %d\n\n", scoreBOS);
			printf("\n*************************************************************\n");

			getchar();
		}
		break;

		case 'Q':
		case 'q':
			break;

		default:
			printf("잘못 입력하셨습니다.\n\n");
			getchar();
		}
	} while (menuChoice != 'Q' && menuChoice != 'q');
}



