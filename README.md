- 👋 Hi, I’m @sobhanagh
//Minesweeper in C//
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <fcntl.h>
#include <io.h>f
#pragma warning (disable:4996)
//2=ghablan click L kardi
//5= flag gozashti
// 4= flag roye bomb hast
//1= bomb dare
//0=khalie
char satr1, soton1;
int satr, soton;

struct ID {
	char name[30];
	int win = 0;
	int loose = 0;
}id;

char n;
char click[1];

void kashtbomb(int bomb2[9][9], int savebomb[9][9]) {
	int f = -1;
	int f1 = -1;
	int f2 = -1;
	//bomb2[9][9] = { 0 };
	int c = 0;
	int c3 = 0;
	int c10 = 0;
	int counte = 0;
	int temp = 0;
	int tbomb = 10;
	int b[10] = { 0 };
	for (int q = 0; q < tbomb; q++) {
		int i = rand() % 9;
		int j = rand() % 9;
		if (b[i] <= 3) {
			b[i]++;
			if (bomb2[i][j] != 1) {
				bomb2[i][j] = 1;
			}
			else {
				if (q > 0) {
					q--;
				}

			}
		}
		else {
			if (q > 0) {
				q--;
			}
		}
	}

	for (int i = 0; i < 9; i++) {
		for (int j = 0; j < 9; j++) {
			savebomb[i][j] = bomb2[i][j];
		}
	}
	for (int i = 0; i < 9; i++) {
		for (int j = 0; j < 9; j++) {
			printf("[%d][%d] = %d", i, j,bomb2[i][j]);
		}
	}

}

int tedadBombDor(int satr, int soton, int bomb3[9][9]) {
	int c = 0;
	if ((satr + 1 <= 9)) {
		if (bomb3[soton][satr + 1] == 1) {
			c++;
		}
	}
	if ((satr - 1) >= 0) {
		if (bomb3[soton][satr - 1] == 1) {
			c++;
		}
	}
	if ((soton + 1) <= 9) {
		if (bomb3[soton + 1][satr] == 1) {
			c++;
		}
	}
	if ((soton - 1) >= 0) {
		if (bomb3[soton - 1][satr] == 1) {
			c++;
		}
	}
	if (((satr + 1) <= 9) && ((soton + 1) <= 9)) {
		if (bomb3[soton + 1][satr + 1] == 1) {
			c++;
		}
	}
	if (((satr - 1) >= 0) && ((soton - 1) >= 0)) {
		if (bomb3[soton - 1][satr - 1] == 1) {
			c++;
		}
	}
	if (((satr + 1) <= 9) && ((soton - 1) >= 0)) {
		if (bomb3[soton - 1][satr + 1] == 1) {
			c++;
		}

	}
	if (((satr - 1) >= 0) && ((soton + 1) <= 9)) {
		if (bomb3[soton + 1][satr - 1] == 1) {
			c++;
		}

	}

	return c;

}
void zaminkarbar(int bomb4[9][9], int flag1, int aclick, int c5, int c6) {
	//int c = 0;
	_setmode(_fileno(stdout), _O_U8TEXT);
	wprintf(L"\033[0;32m \n\x2660 : %d  \n\n", flag1);
	/*_setmode(_fileno(stdout), _O_U8TEXT);
	wprintf(L"\x01A0 : %d \n", tbomb);*/
	wprintf(L"\033[0;33m 0 1 2 3 4 5 6 7 8 \n");
	for (int i = 0; i < 9; i++) {
		for (int j = 0; j < 9; j++) {
			if (c5 == 0) {
				wprintf(L"\033[0;33m|");
				wprintf(L"\033[0;33m-");
				//wprintf(L"|");
			}
			else if (bomb4[i][j] == 1) {
				if (c6 == 0) {
					if (aclick == 82) {
						wprintf(L"\033[0;33m|");
						_setmode(_fileno(stdout), _O_U8TEXT);
						wprintf(L"\033[0;32m\x2660");
						bomb4[i][j] = 5;
					}
					else {
						wprintf(L"\033[0;33m|");
						wprintf(L"%d", tedadBombDor(i, j, bomb4));
					}
				}
				else {
					wprintf(L"\033[0;33m|");
					wprintf(L"\033[0;33m-");
				}

			}
			else if (bomb4[i][j] == 2) {
				wprintf(L"\033[0;33m|");
				wprintf(L"\033[0;31m%d", tedadBombDor(j, i, bomb4));
			}
			else if (bomb4[i][j] == 5) {
				wprintf(L"\033[0;33m|");
				_setmode(_fileno(stdout), _O_U8TEXT);
				wprintf(L"\033[0;32m\x2660");
			}

			else {
				//wprintf(L"-");
				//wprintf(L"|");
				wprintf(L"\033[0;33m|");
				wprintf(L"\033[0;33m-");
			}
		}
		if (c5 == 0) {
			wprintf(L"\033[0;33m|");
		}
		else {
			wprintf(L"\033[0;33m|");
		}
		if (i == 0) {
			wprintf(L"\033[0;33m 0 ");
		}
		if (i == 1) {
			wprintf(L"\033[0;33m 1 ");
		}
		if (i == 2) {
			wprintf(L"\033[0;33m 2 ");
		}
		if (i == 3) {
			wprintf(L"\033[0;33m 3 ");
		}
		if (i == 4) {
			wprintf(L"\033[0;33m 4 ");
		}
		if (i == 5) {
			wprintf(L"\033[0;33m 5 ");
		}
		if (i == 6) {
			wprintf(L"\033[0;33m 6 ");
		}
		if (i == 7) {
			wprintf(L"\033[0;33m 7 ");
		}
		if (i == 8) {
			wprintf(L"\033[0;33m 8 ");
		}
		wprintf(L"\n");
	}

}


int zamin(int c10) {
tag10:	int tbomb = 10;
	int a; // bara inke click int beshe
	//char satr1, soton1;
	//int satr, soton;
	//char click[1];
	int flag = 10;
	int savebomb[9][9] = { 0 };
	int bomb[9][9] = { 0 };
	kashtbomb(bomb, savebomb);
	int flagbomb = 0;
	int c6 = 0;
	int c5 = 0; //bara inke avalin bar zamin khali chap kone
	if (c10 > 0) {
		//int n;
		//char n;
		system("cls||clear");
	tag30:	wprintf(L"\033[0;35mplease enter your name :\n");
		//gets_s(name);
		scanf("%s", id.name);
		for (int i = 0, c8 = 0; i < strlen(id.name); i++, c8++) {
			if (c8 == 0) {
				wprintf(L"\033[0;36mHello ");
			}
			wprintf(L"\033[0;36m%c", id.name[i]);
		}
		wprintf(L"\n");
		wprintf(L"\033[0;35mif you want change your name press 1 if not press 2\n");
		wprintf(L"\033[0;36m1_ Change Name\n2_ play!\n");
		//gets_s(menu); 
	tag20:	scanf("%s", &n);
		if (n == '2') {
			goto tag3;
		}
		else if (n == '1') {
			goto tag30;
		}
		else {
			wprintf(L"\033[0;31meshtebah vared kardi,dobare bezan\n");
			goto tag20;
		}

	}
	while (1) {
	tag3:		a = click[0];
		int aclick = click[0];
		zaminkarbar(bomb, flag, aclick, c5, c6);
		c6++;
		c5++;

		if (flagbomb == 10) {
			id.win++;
			wprintf(L"\033[0;36myou win!!!\nwin : %d\nloose : %d\n", id.win, id.loose);
			break;
		}

	tag:		scanf("%s%s%s", &satr1, &soton1, &click);

		satr = satr1;
		soton = soton1;
		satr = satr - 48;
		soton = soton - 48;
		//int satr1 = satr ;
		//int soton1 = soton ;
		a = click[0];

		//check motabar
		if (satr < 0 || satr >= 9) {
			wprintf(L"\033[0;31mtedad soton ro eshtebah vared kardi, dobare vared kon\n");
			goto tag;
		}
		if (soton < 0 || soton >= 9) {
			wprintf(L"\033[0;31mtedad satr ro eshtebah vared kardi, dobare vared kon\n");
			goto tag;
		}
		if (bomb[soton][satr] == 2) {
			wprintf(L"\033[0;31mghablan click L kardi, dobare vared kon");
			goto tag;
		}
		if (a == 82 || a == 76) {
			goto tag2;
		}
		else {
			wprintf(L"\033[0;31mcaracter ro eshtebah vared kardi, dobare vared kon\n");
			goto tag;
		}
	tag2:		//R click
		a = click[0];
		if (a == 82) {
			if (flag != 0) {
				if (bomb[soton][satr] == 5) {
					//ghablan parcham gozashti
					bomb[soton][satr] = savebomb[soton][satr];
					flag++;
					goto tag3;
				}
				else if (bomb[soton][satr] == 1) {
					tbomb--;
					flagbomb++;
					if (flag != 0) {
						flag--;
					}

					bomb[soton][satr] = 5;
				}
				else if (bomb[soton][satr] == 0) {
					if (flag != 0) {
						flag--;
					}
					bomb[soton][satr] = 5;
				}
			}
			else {
				wprintf(L"\033[0;31mtedad flag tamom shode!!!!\n");
			}
		}
		// L click
		else {
			a = click[0];
			if (bomb[soton][satr] == 5 && a == 76) {
				//wprintf(L"ghablan parcham gozashti , dobare vared kon\x2660\n");
				bomb[soton][satr] = savebomb[soton][satr];
				goto tag;
			}
			if (bomb[soton][satr] == 1 && a == 76) {
				_setmode(_fileno(stdout), _O_U8TEXT);
				wprintf(L"\033[0;31mthere was a bomb!! you lose \x01A0\n");
				id.loose++;
				for (int i = 0; i < 9; i++) {
					for (int j = 0; j < 9; j++) {
						if (bomb[i][j] == 5) {
							wprintf(L"\033[0;31m|");
							_setmode(_fileno(stdout), _O_U8TEXT);
							wprintf(L"\033[0;32m\x2660");
						}
						else if (bomb[i][j] == 1) {
							wprintf(L"\033[0;31m|");
							_setmode(_fileno(stdout), _O_U8TEXT);
							wprintf(L"\033[0;33m\x01A0");
						}
						else {
							wprintf(L"\033[0;31m|");
							wprintf(L"\033[0;31m-");
						}
					}
					wprintf(L"\033[0;31m|\n");
				}
				a = click[0];
				break;
			}
			else if (bomb[soton][satr] == 0 && a == 76) {
				bomb[soton][satr] = 2; // 2 yani ghablan L click shode va bomb nabode
				//age bazam L kone hamon ghabli chap beshe
			}
		}
	}
	a = click[0];
	wprintf(L"\033[0;36mwin : %d\nloose : %d\n\n", id.win, id.loose);
	return 1;
}



//12 * 12

void kashtbomb2(int bomb2[13][13], int savebomb[13][13]) {
	int f = -1;
	int f1 = -1;
	int f2 = -1;
	//bomb2[9][9] = { 0 };
	int c = 0;
	int c3 = 0;
	int c10 = 0;
	int temp = 0;
	int tbomb = 20;
	int b[12] = { 0 };
	for (int q = 0; q < tbomb; q++) {
		int i = rand() % 12;
		int j = rand() % 12;
		if (b[i] <= 3) {
			b[i]++;
			if (bomb2[i][j] != 1) {
				bomb2[i][j] = 1;
			}
			else {
				if (q > 0) {
					q--;
				}

			}
		}
		else {
			if (q > 0) {
				q--;
			}
		}
	}

	for (int i = 0; i < 12; i++) {
		for (int j = 0; j < 12; j++) {
			savebomb[i][j] = bomb2[i][j];
		}
	}

}

int tedadBombDor2(int satr, int soton, int bomb3[13][13]) {
	int c = 0;
	if ((satr + 1 <= 12)) {
		if (bomb3[soton][satr + 1] == 1) {
			c++;
		}
	}
	if ((satr - 1) >= 0) {
		if (bomb3[soton][satr - 1] == 1) {
			c++;
		}
	}
	if ((soton + 1) <= 12) {
		if (bomb3[soton + 1][satr] == 1) {
			c++;
		}
	}
	if ((soton - 1) >= 0) {
		if (bomb3[soton - 1][satr] == 1) {
			c++;
		}
	}
	if (((satr + 1) <= 12) && ((soton + 1) <= 12)) {
		if (bomb3[soton + 1][satr + 1] == 1) {
			c++;
		}
	}
	if (((satr - 1) >= 0) && ((soton - 1) >= 0)) {
		if (bomb3[soton - 1][satr - 1] == 1) {
			c++;
		}
	}
	if (((satr + 1) <= 12) && ((soton - 1) >= 0)) {
		if (bomb3[soton - 1][satr + 1] == 1) {
			c++;
		}

	}
	if (((satr - 1) >= 0) && ((soton + 1) <= 12)) {
		if (bomb3[soton + 1][satr - 1] == 1) {
			c++;
		}

	}

	return c;

}
void zaminkarbar2(int bomb4[13][13], int flag1, int aclick, int c5, int c6) {
	//int c = 0;
	_setmode(_fileno(stdout), _O_U8TEXT);
	wprintf(L"\033[0;32m \n\x2660 : %d  \n\n", flag1);
	/*_setmode(_fileno(stdout), _O_U8TEXT);
	wprintf(L"\x01A0 : %d \n", tbomb);*/
	wprintf(L"\033[0;33m 0 1 2 3 4 5 6 7 8 9 10 11 \n");
	for (int i = 0; i < 12; i++) {
		for (int j = 0; j < 12; j++) {
			if (c5 == 0) {
				wprintf(L"\033[0;33m|");
				wprintf(L"\033[0;33m-");
				//wprintf(L"|");
			}
			else if (bomb4[i][j] == 1) {
				if (c6 == 0) {
					if (aclick == 82) {
						wprintf(L"\033[0;33m|");
						_setmode(_fileno(stdout), _O_U8TEXT);
						wprintf(L"\033[0;32m\x2660");
						bomb4[i][j] = 5;
					}
					else {
						wprintf(L"\033[0;33m|");
						wprintf(L"%d", tedadBombDor2(i, j, bomb4));
					}
				}
				else {
					wprintf(L"\033[0;33m|");
					wprintf(L"\033[0;33m-");
				}

			}
			else if (bomb4[i][j] == 2) {
				wprintf(L"\033[0;33m|");
				wprintf(L"\033[0;31m%d", tedadBombDor2(j, i, bomb4));
			}
			else if (bomb4[i][j] == 5) {
				wprintf(L"\033[0;33m|");
				_setmode(_fileno(stdout), _O_U8TEXT);
				wprintf(L"\033[0;32m\x2660");
			}

			else {
				//wprintf(L"-");
				//wprintf(L"|");
				wprintf(L"\033[0;33m|");
				wprintf(L"\033[0;33m-");
			}
		}
		if (c5 == 0) {
			wprintf(L"\033[0;33m|");
		}
		else {
			wprintf(L"\033[0;33m|");
		}
		if (i == 0) {
			wprintf(L"\033[0;33m 0 ");
		}
		if (i == 1) {
			wprintf(L"\033[0;33m 1 ");
		}
		if (i == 2) {
			wprintf(L"\033[0;33m 2 ");
		}
		if (i == 3) {
			wprintf(L"\033[0;33m 3 ");
		}
		if (i == 4) {
			wprintf(L"\033[0;33m 4 ");
		}
		if (i == 5) {
			wprintf(L"\033[0;33m 5 ");
		}
		if (i == 6) {
			wprintf(L"\033[0;33m 6 ");
		}
		if (i == 7) {
			wprintf(L"\033[0;33m 7 ");
		}
		if (i == 8) {
			wprintf(L"\033[0;33m 8 ");
		}
		if (i == 9) {
			wprintf(L"\033[0;33m 9");
		}
		if (i == 10) {
			wprintf(L"\033[0;33m 10");
		}
		if (i == 11) {
			wprintf(L"\033[0;33m 11 ");
		}
		wprintf(L"\n");
	}

}



int zamin2(int c10) {
tag10:	int tbomb = 20;
	int a; // bara inke click int beshe
	//int satr, soton;
	//char click[1];
	int flag = 20;
	int savebomb[13][13] = { 0 };
	int bomb[13][13] = { 0 };
	kashtbomb2(bomb, savebomb);
	int flagbomb = 0;
	int c6 = 0;
	int c5 = 0; //bara inke avalin bar zamin khali chap kone
	if (c10 > 0) {
		//int n;
		//char n;
		system("cls||clear");
	tag30:	wprintf(L"\033[0;35mplease enter your name :\n");
		//gets_s(name);
		scanf("%s", id.name);
		for (int i = 0, c8 = 0; i < strlen(id.name); i++, c8++) {
			if (c8 == 0) {
				wprintf(L"\033[0;36mHello ");
			}
			wprintf(L"\033[0;36m%c", id.name[i]);
		}
		wprintf(L"\n");
		wprintf(L"\033[0;35mif you want change your name press 1 if not press 2\n");
		wprintf(L"\033[0;36m1_ Change Name\n2_ play!\n");
		//gets_s(menu); 
	tag20:	scanf("%s", &n);
		if (n == '2') {
			goto tag3;
		}
		else if (n == '1') {
			goto tag30;
		}
		else {
			wprintf(L"\033[0;31meshtebah vared kardi,dobare bezan\n");
			goto tag20;
		}

	}
	while (1) {
	tag3:		a = click[0];
		int aclick = click[0];
		zaminkarbar2(bomb, flag, aclick, c5, c6);
		c6++;
		c5++;

		if (flagbomb == 20) {
			id.win++;
			wprintf(L"you win!!!\nwin : %d\nloose : %d\n", id.win, id.loose);
			break;
		}

	tag:		scanf("%s%s%s", &satr1, &soton1, &click);
		//satr--;
		//soton--;
		satr = satr1;
		soton = soton1;
		satr = satr - 48;
		soton = soton - 48;
		a = click[0];
		//check motabar
		if (satr < 0 || satr >= 12) {
			wprintf(L"\033[0;31mtedad soton ro eshtebah vared kardi, dobare vared kon\n");
			goto tag;
		}
		if (soton < 0 || soton >= 12) {
			wprintf(L"\033[0;31mtedad satr ro eshtebah vared kardi, dobare vared kon\n");
			goto tag;
		}
		if (bomb[soton][satr] == 2) {
			wprintf(L"\033[0;31mghablan click L kardi, dobare vared kon");
			goto tag;
		}
		if (a == 82 || a == 76) {
			goto tag2;
		}
		else {
			wprintf(L"\033[0;31mcaracter ro eshtebah vared kardi, dobare vared kon\n");
			goto tag;
		}
	tag2:		//R click
		a = click[0];
		if (a == 82) {
			if (flag != 0) {
				if (bomb[soton][satr] == 5) {
					//ghablan parcham gozashti
					bomb[soton][satr] = savebomb[soton][satr];
					flag++;
					goto tag3;
				}
				else if (bomb[soton][satr] == 1) {
					tbomb--;
					flagbomb++;
					if (flag != 0) {
						flag--;
					}

					bomb[soton][satr] = 5;
				}
				else if (bomb[soton][satr] == 0) {
					if (flag != 0) {
						flag--;
					}
					bomb[soton][satr] = 5;
				}
			}
			else {
				wprintf(L"\033[0;31mtedad flag tamom shode!!!!\n");
			}
		}
		// L click
		else {
			a = click[0];
			if (bomb[soton][satr] == 5 && a == 76) {
				//wprintf(L"ghablan parcham gozashti , dobare vared kon\x2660\n");
				bomb[soton][satr] = savebomb[soton][satr];
				goto tag;
			}
			if (bomb[soton][satr] == 1 && a == 76) {
				_setmode(_fileno(stdout), _O_U8TEXT);
				wprintf(L"\033[0;31mthere was a bomb!! you lose \x01A0\n");
				id.loose++;
				for (int i = 0; i < 12; i++) {
					for (int j = 0; j < 12; j++) {
						if (bomb[i][j] == 5) { ////////////////////////
							wprintf(L"\033[0;31m|");
							_setmode(_fileno(stdout), _O_U8TEXT);
							wprintf(L"\033[0;32m\x2660");
						}
						else if (bomb[i][j] == 1) {
							wprintf(L"\033[0;31m|");
							_setmode(_fileno(stdout), _O_U8TEXT);
							wprintf(L"\033[0;33m\x01A0");
						}
						else {
							wprintf(L"\033[0;31m|");
							wprintf(L"\033[0;31m-");
						}
					}
					wprintf(L"\033[0;31m|\n");
				}
				a = click[0];
				break;
			}
			else if (bomb[soton][satr] == 0 && a == 76) {
				bomb[soton][satr] = 2; // 2 yani ghablan L click shode va bomb nabode
				//age bazam L kone hamon ghabli chap beshe
				//wprintf(L"around of the home that you click have : %d bomb\n", tedadBombDor(satr, soton, bomb));
				//bomb[soton][satr] = tedadBombDor(satr, soton, bomb);
			}
		}
	}
	a = click[0];
	wprintf(L"\033[0;36mwin : %d\nloose : %d\n\n", id.win, id.loose);
	return 1;
}









char n2;
char rematch;
int main() {
	srand(time(NULL));
	//	char name[30];
	int c10 = 0;
	int c11 = 0;
	//int n;
	//char n;
tag3:	printf("\033[0;35mplease enter your name :\n");
	scanf("%s", id.name);
	printf("\033[0;36mHello %s\n", id.name);
	printf("\033[0;35mif you want change your name press 1 if not press 2\n");
	printf("\033[0;36m1_ Change Name\n2_ play!\n");
tag:	scanf("%s", &n);
	if (n == '2') {
		printf("choose one item :\n1_ 9 * 9\n2_ 12 * 12\n");
		scanf("%s", &n2);
		if (n2 == '1') {
			printf("\033[0;35ttedad bomb : 10\n");
		tag9:		if (zamin(c10) == 1) {
			wprintf(L"\033[0;35mif you want play again prees 1 else press 2\n");
		tag11:			scanf("%s", &rematch);
			if (rematch == '1') {
				c10++;
				goto tag9;
			}
			else if (rematch == '2') {
				for (int i = 0, c21 = 0; i < strlen(id.name); i++, c21++) {
					if (c21 == 0) {
						wprintf(L"\033[0;36mgoodby ");
					}
					wprintf(L"\033[0;36m%c", id.name[i]);
				}
			}
			else {
				wprintf(L"\033[0;31m eshtebah vared kardi!!!,dobare bezan\n");
				goto tag11;
			}
		}
		}
		else if (n2 == '2') {
			printf("\033[0;35ttedad bomb : 20\n");
		tag90:		if (zamin2(c11) == 1) {
			wprintf(L"\033[0;35mif you want play again prees 1 else press 2\n");
		tag110:			scanf("%s", &rematch);
			if (rematch == '1') {
				c11++;
				goto tag90;
			}
			else if (rematch == '2') {
				for (int i = 0, c21 = 0; i < strlen(id.name); i++, c21++) {
					if (c21 == 0) {
						wprintf(L"\033[0;36mgoodby ");
					}
					wprintf(L"\033[0;36m%c", id.name[i]);
				}
			}
			else {
				wprintf(L"\033[0;31m eshtebah vared kardi!!!,dobare bezan\n");
				goto tag110;
			}
		}
		}
	}
	else if (n == '1') {
		goto tag3;
	}
	else {
		wprintf(L"\033[0;31meshtebah vared kardi,dobare bezan\n");
		goto tag;
	}
}







