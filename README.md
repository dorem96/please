# please
/***********************************
 **   볼링 점수 계산 프로그램     **
 **    작성자 : 송승우            **
 **    작성일 : 2016년 5월 10일   **
 ***********************************/
#include <stdio.h>
int main(void)
{
	int frame=1, turn, score=0, total=0, strike=0, spr=0, spare=0, bonus=0;
	while(frame<=10)
	{
		score=0;
		spare=0;
		turn=1;
		while(turn<3)
		{
			bonus=1;
			if(strike>0)
			{
				bonus+=1;
					if(strike>2)
					{
						bonus+=1;
						strike--;
					}
				strike--;
			}
			if(spr==1)
			{
				bonus+=1;
				spr=0;
			}
			if(frame<10)
			{
			printf("%d frame %d turn : ", frame, turn);
			scanf("%d", &score);
			total+=(score*bonus);
			spare+=score;
			turn++;
			printf("**** now score : %d\n", total);
			if(score==10)
			{	
				strike+=2;
				turn=3;
			}
			else if(spare==10)
				spr=1;
			}
			else if(frame==10)
			{
				printf("%d frame %d turn : ", frame, turn);
				scanf("%d", &score);
				total+=(score*bonus);
				spare+=score;
				if(spare==10)
					spr=2;
				if(turn==1)
					printf("****now score : %d\n", total);
				if(turn==2)
				{
						if(spr==0)
							printf("****final score : %d\n", total);
						else if(spr==2)
							printf("****now score : %d\n", total);
				}
			turn++;
			}
		}
		frame++;
	}
		if(spr==2)
		{
			printf("10 frame 3 turn : ");
			scanf("%d", &score);
			total+=score;
			printf("****final score : %d", total);
		}
		return 0;
	}
