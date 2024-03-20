#include<stdio.h>
#include<windows.h>
#include<conio.h>
#include<time.h>

    int obsX=0,obsY=0;
    int bugX1=0,bugX2=0,bugX3=0,bugX4=0,bugX5=0,bugX6=0,bugY=0;

    // STRUCTURE FOR LEADERBOARD-----------------------------------
struct player{
    char name[25];
    int score;

};
void updateLeaderboard(const char *name, int score) {
    FILE *lb;
    struct player leaderboard[10];

    // Read current leaderboard data
    lb = fopen("leaderboard.txt", "r");
    if (lb == NULL) {
        lb = fopen("leaderboard.txt", "w");
        fclose(lb);
        return;
    }

    for (int i = 0; i < 10; i++) {
        if (fscanf(lb, "%s %d", leaderboard[i].name, &leaderboard[i].score) != 2) {
            strcpy(leaderboard[i].name, "Default");
            leaderboard[i].score = 0;
        }
    }
    fclose(lb);

    // Insert the new player's data
    strcpy(leaderboard[9].name, name);
    leaderboard[9].score = score;

    // Sort the leaderboard array in descending order based on scores
    for (int i = 0; i < 9; i++) {
        for (int j = 0; j < 9 - i; j++) {
            if (leaderboard[j].score < leaderboard[j + 1].score) {
                struct player temp = leaderboard[j];
                leaderboard[j] = leaderboard[j + 1];
                leaderboard[j + 1] = temp;
            }
        }
    }

    // Write the updated leaderboard data back to the file
    lb = fopen("leaderboard.txt", "w");
    for (int i = 0; i < 10; i++) {
        fprintf(lb, "%s %d\n", leaderboard[i].name, leaderboard[i].score);
    }
    fclose(lb);
}
//FOR GETTING RANDOM NUMBER FOR OBSTACLE-----------------------------

int getRandomNumber(int min, int max) {
    // Seed the random number generator with the current time
    srand(time(NULL));
    // Generate a random number within the specified range
    int randomNumber = rand() % (max - min + 2) + min;
    return randomNumber;
}

//FOR GO TO X Y CO-ORDINATES-----------------------------------------

void gotoxy(int x, int y) {
    COORD coord;
    coord.X = x;
    coord.Y = y;
    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), coord);
}

//FOR COLOR----------------------------------------------------------

void setcolor(int color) {
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), color);
}

// FOR TEXT COLOR----------------------------------------------------

    void textcolor(int color) {
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), color);
}
    // BORDER
    void border(){
    setcolor(1);
    for(int i=1;i<=80;i++) {
        printf("%c",254);fflush(stdout);
    }
    for(int i=1;i<=26;i++) {
        printf("%c\n",254);fflush(stdout);
    }
    for(int i=1;i<=25;i++) {
        gotoxy(80, i);
        printf("%c",254);fflush(stdout);
    }
    for(int i=1;i<=80;i++) {
        gotoxy(i, 25);
        printf("%c",254);fflush(stdout);
    }

}
    // front page-----------------------------------------------------
    void front_page()
{
    setcolor(1);
    for(int i=1;i<=80;i++) {
        printf("%c",254);fflush(stdout);
    }
    for(int i=1;i<=26;i++) {
        printf("%c\n",254);fflush(stdout);
    }
    for(int i=1;i<=25;i++) {
        gotoxy(80, i);
        printf("%c",254);fflush(stdout);
    }
    for(int i=1;i<=80;i++) {
        gotoxy(i, 25);
        printf("%c",254);fflush(stdout);
    }
    // bugrunner
    int x,y,n;
    int i;
    setcolor(1);///B
    x=13,y=15;
    for(i=1;i<=5;i++) {
        gotoxy(x,y-i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
   x=14,y=10;
    for(int i=0;i<=3;i++) {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=17,y=10;
    for(i=1;i<=2;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=17,y=12;
     for(i=1;i<=2;i++)
    {
        gotoxy(x-i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=17,y=12;
    for(i=1;i<=2;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=17,y=14;
    for(i=1;i<=3;i++)
    {
        gotoxy(x-i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    setcolor(2);///U
    x=19,y=9;
    for(i=1;i<=4;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=19,y=14;
    for(i=1;i<=2;i++)
    {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=22,y=14;
    for(i=1;i<=4;i++)
    {
        gotoxy(x,y-i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    setcolor(3);///G
    x=23,y=10;
    for(i=1;i<=4;i++)
    {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=24,y=10;
    for(i=1;i<=4;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    y=14,x=24;
    for(i=1;i<=3;i++)
    {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=28,y=13;
    for(i=1;i<=1;i++)
    {
        gotoxy(x,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=28,y=12;
    for(i=1;i<=1;i++)
    {
        gotoxy(x,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=27,y=12;
    for(i=1;i<=3;i++)
    {
        gotoxy(x,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    setcolor(4);///R
    x=30,y=10;
    for(i=1;i<=3;i++)
    {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=30,y=10;
    for(i=1;i<=4;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=33,y=10;
    for(i=1;i<=2;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=31,y=12;
    for(i=1;i<=1;i++)
    {
        gotoxy(x,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=31,y=12;
     for(i=1;i<=2;i++)
    {
        usleep(0);
        gotoxy(x+i,y+i);
        printf("%c",220);fflush(stdout);
    }
    setcolor(5);///U
    x=36,y=9;
    for(i=1;i<=5;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=36,y=14;
    for(i=1;i<=3;i++)
    {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=39,y=15;
    for(i=1;i<=5;i++)
    {
        gotoxy(x,y-i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    setcolor(6);///N
    x=41,y=9;
     for(i=1;i<=5;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=41,y=9;
     for(i=1;i<=5;i++)
    {
        gotoxy(x+i,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=46,y=14;
     for(i=1;i<=4;i++)
    {
        gotoxy(x,y-i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    setcolor(7);///N
    x=48,y=9;
     for(i=1;i<=5;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=48,y=9;
     for(i=1;i<=5;i++)
    {
        gotoxy(x+i,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=53,y=14;
     for(i=1;i<=4;i++)
    {
        gotoxy(x,y-i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    setcolor(8);///E
    x=55,y=10;
     for(i=1;i<=4;i++)
    {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=55,y=9;
     for(i=1;i<=5;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=55,y=12;
     for(i=1;i<=4;i++)
    {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=55,y=14;
     for(i=1;i<=4;i++)
    {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    setcolor(9);///R
    x=61,y=10;
    //x=23,y=9;
    for(i=1;i<=3;i++)
    {
        gotoxy(x+i,y);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }

    x=61,y=10;
    for(i=1;i<=4;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=64,y=10;
    //x=24,y=11;
    for(i=1;i<=2;i++)
    {
        gotoxy(x,y+i);
        printf("%c",220);
        usleep(0);
        fflush(stdout);
    }
    x=64,y=12;
    //x=24,y=11;
     for(i=1;i<=2;i++)
    {
        usleep(0);
        gotoxy(x-i,y);
        printf("%c",220);fflush(stdout);
    }
    x=62,y=12;
    for(i=1;i<=2;i++)
    {
        usleep(0);
        gotoxy(x+i,y+i);
        printf("%c",220);fflush(stdout);
    }

    setcolor(2);
    gotoxy(13,17);
    printf("Press any key to continue");
    getch();
}
    //FOR DISPLAY MENU-----------------------------------------------

    void display_menu()
{
system("cls");
//border----------
setcolor(1);
    for(int i=1;i<=80;i++) {
        printf("%c",254);fflush(stdout);
    }
    for(int i=1;i<=26;i++) {
        printf("%c\n",254);fflush(stdout);
    }
    for(int i=1;i<=25;i++) {
        gotoxy(80, i);
        printf("%c",254);fflush(stdout);
    }
    for(int i=1;i<=80;i++) {
        gotoxy(i, 25);
        printf("%c",254);fflush(stdout);
    }

gotoxy(10, 5);
setcolor(12);
printf("Welcome to BugRunner!");fflush(stdout);

gotoxy(10, 7);
setcolor(14);
printf("1. Play");fflush(stdout);

gotoxy(10, 8);
setcolor(14);
printf("2. Leaderboard");fflush(stdout);

gotoxy(10, 9);
setcolor(14);
printf("3. Exit");fflush(stdout);

gotoxy(10, 13);
setcolor(15);
printf("Choose Option : ");fflush(stdout);
}

    // FOR PRINTINF OBSTACLE-----------------------------------------

    void obstacle(int x,int y){
        //for obstacle 1
        setcolor(5);
        gotoxy(4+x,1+y);
        printf("%c",219); fflush(stdout);
        setcolor(15);
        gotoxy(3+x,2+y);
        printf("%c",219); fflush(stdout);
        gotoxy(4+x,2+y);
        printf("%c",219); fflush(stdout);
        gotoxy(5+x,2+y);
        printf("%c",219); fflush(stdout);
        setcolor(5);
        //--------------------
        obsX=x+4;
        obsY=y+3;
        //--------------------
        gotoxy(4+x,3+y);
        printf("%c",219); fflush(stdout);
        // for getting rid of obstacle 1
        Sleep(50);
        setcolor(5);
        gotoxy(4+x,1+y);
        printf(" "); fflush(stdout);
        setcolor(15);
        gotoxy(3+x,2+y);
        printf(" "); fflush(stdout);
        gotoxy(4+x,2+y);
        printf(" "); fflush(stdout);
        gotoxy(5+x,2+y);
        printf(" "); fflush(stdout);
        setcolor(5);
        gotoxy(4+x,3+y);
        printf(" "); fflush(stdout);



    }

    //FOR PRINTING THE MAIN GAME SCREEEN-----------------------------

    void screen(int p,int q){
    // for border
    setcolor(1);
    for(int i=1;i<=80;i++) {
        printf("%c",254);fflush(stdout);
    }
    for(int i=1;i<=26;i++) {
        printf("%c\n",254);fflush(stdout);
    }
    for(int i=1;i<=25;i++) {
        gotoxy(80, i);
        printf("%c",254);fflush(stdout);
    }
    for(int i=1;i<=80;i++) {
        gotoxy(i, 25);
        printf("%c",254);fflush(stdout);
    }
    setcolor(1); // partition
    for(int i=1;i<=24;i++){
        gotoxy(45, i);
        printf("%c",254);fflush(stdout);
    }

    // FOR PRINTING THE BUG-----------------------------------------

    setcolor(15); // for white color
    gotoxy(2+p, 21);
    printf("%c",254);fflush(stdout);

    setcolor(4); // for red color
    bugX1=2+p;
    bugY=9+q;
    gotoxy(2+p, q+9); printf("%c",254); fflush(stdout);
    bugX2=1+p;
    gotoxy(1+p, q+10); printf("%c",254);fflush(stdout);
    bugX3=2+p;
    gotoxy(2+p, q+10); printf("%c",254);fflush(stdout);
    bugX4=3+p;
    gotoxy(3+p, q+10); printf("%c",254);fflush(stdout);
    bugX5=3+p;
    gotoxy(3+p, q+11); printf("%c",254);fflush(stdout);
    bugX6=1+p;
    gotoxy(1+p, q+11); printf("%c",254);fflush(stdout);
    gotoxy(1+p, q+12); printf("%c",254);fflush(stdout);
    gotoxy(2+p, q+12); printf("%c",254);fflush(stdout);
    gotoxy(3+p, q+12); printf("%c",254);fflush(stdout);
    gotoxy(2+p, q+13); printf("%c",254);fflush(stdout);
    }

    // FOR PRINTING GAME OVER ANIMATION------------------------------

    void gameover()
{
    int a,b,time=30;
    setcolor(14);
    for(a=13,b=7;b>5;a-=2,b--) //<---game
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
    }
    for(a=10,b=6;a>7;a--)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
    }
     for(a=6,b=7;b<11;b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=8,b=11;a<11;a++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=10,b=10;b>8;b--)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=11,b=9;a<14;a++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=13,b=10;b<12;b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=16,b=10;b>9;b--)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=17,b=9;a<20;a++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=20,b=10;b<11;b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=19,b=11;a>16;a--)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=21,b=11;b<12;b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=23,b=11;b>9;b--)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=22,b=9;b>8;b--)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=25,b=9;a<27;a++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=27,b=10;b<12;b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=29,b=9;a<31;a++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=31,b=10;b<12;b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=34,b=9;a<39;a+=2)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=37,b=8;a>34;a-=2)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=34,b=10;b<11;b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=35,b=11;a<39;a+=2)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=16,b=14;a>13;a-=2,b--) //<<----over
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=12,b=13;a>9;a-=2,b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=10,b=15;a<13;a+=2,b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=14,b=16;a<17;a+=2,b--)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=18,b=13;a<22;a++,b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=22,b=16;b>12;a++,b--)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=27,b=14;a<32;a+=2)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=30,b=13;a>27;a-=2)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=27,b=15;b<16;b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=28,b=16;a<31;a+=2)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=33,b=13;a<35;a++,b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=34,b=15;b<17;b++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
    for(a=36,b=13;a<38;a++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
   for(a=38,b=14;a<39;a++)
    {
        gotoxy(a,b);
        printf("%c",220); fflush(stdout);
        Sleep(time);
   }
}
int main() {
    //FOR DISPLAY
    front_page();
    jump: ;
    int flag=0,key=0;
    int x=0,y=0; // for obstacle------------------------------------
    int p=20,q=10; // for bug---------------------------------------
    int forscore =0,score=0,highscore=0;    // for score------------------------

    //OPTION CHOICE--------------------------------
    int choice;
    char name[10];
    int exit=0;

        while(1){
        display_menu();
        scanf("%d",&choice);
        if(choice==1){
            gotoxy(10,15);
            printf("Enter your name : ");
            scanf("%s",name);
            system("cls");
            break;
        }
        else if(choice==2){
            system("cls");
            border();
            struct player player[10];
            FILE *lb;
            lb = fopen("leaderboard.txt","r");
            if(lb==0){
                lb=fopen("leaderboard.txt","w");
                fclose(lb);
                for (int i = 0; i < 10; i++) {
                    if (fscanf(lb, "%s %d", player[i].name, &player[i].score) != 2) {

                        strcpy(player[i].name, "Default");
                        player[i].score = 0;
        }
    }
            }
            else{
                setcolor(15);
                for(int i=0;i<10;i++){
                     gotoxy(5,i+3);
                    fscanf(lb,"%s %d",player[i].name, &player[i].score);
                    printf("%s %d\n",player[i].name, player[i].score);
                }
                fclose(lb);
                gotoxy(5,15);
                setcolor(2);
                printf("Press any key to continue---\n");
                getch();
            }

        }
        else if(choice==3){
            exit=1;
            break;
        }
    }

    FILE *fp;

    screen(p,q);
    while(1){
        if(exit){
            system("cls");
            break;
        }
        else {

            setcolor(14);
            gotoxy(51, 2);
            printf("%s is playing now!",name);
            gotoxy(50, 5);
            printf(" SCORE : %d",score);

            fp=fopen("highscore.txt","r");
        if(fp==0){
            fp=fopen("highscore.txt","w");
            fprintf(fp,"%d",highscore);
            fclose(fp);
        }
        fscanf(fp,"%d",&highscore);
        fclose(fp);

            gotoxy(51, 7);
            printf("HIGH SCORE : %d",highscore);

            if(forscore%10==0){
                score++;
            }
            int min=1, max=26;
            if(y==22){
                y=0;
                x=getRandomNumber(min, max);
            }
           forscore++;

           obstacle(x,y);
           y++;

            //FOR CONTROL-------------------------------------------

            if(_kbhit()){
            key= getch();
            if(key =='d'){
                if(p<40){
                    p+=2;
                }
            }
            if(key =='a'){
                if(p>2){
                    p-=2;
                }
            }
            if(p>0 && p<42){

                system("cls");
                screen(p,q);

            }
        }
        // FOR TESTING PURPOSE------------------------------------------------------
        //gotoxy(20,10);
        //printf("%d %d %d %d",bugX1,bugX2,bugX3,bugY);
        //gotoxy(20,12);
        //printf("%d %d",obsX,obsY);
        //--------------------------------------------------------------------------

        if( (bugX1==obsX || bugX2==obsX || bugX3==obsX || bugX4==obsX || bugX5==obsX || bugX6==obsX ) && (obsY==19 || obsY==20 || obsY==21) ){
            system("cls");
            break;

        }
    }
        }
        //GAME OVER----------------------------------------------------------------------

        if(!exit){
            screen(p,q);
        gameover();
        setcolor(14);
        gotoxy(50, 3);
        printf(" SCORE : %d",score);

        // HIGHSCORE SHOW-----------------------------------------------------------------
        if(score>highscore){
            highscore=score;
            fp=fopen("highscore.txt","w");
            fprintf(fp,"%d",highscore);
            fclose(fp);
        }
        gotoxy(51, 5);
        printf("HIGH-SCORE : %d",highscore);

        fclose(fp);
    // for leaderboard
    updateLeaderboard(name, score);

    // FOR GETTING RID OF SYSTEM MESSAGES BEFORE ENDING-----------------------------------
    setcolor(15);
    Sleep(1500);
    getch();
    system("cls");
    gotoxy(25,5);
    setcolor(2);
    printf("Returning to main menu!\n");
    Sleep(3000);
    goto jump;
    }
    setcolor(2);
    gotoxy(25,5);
    printf("---------THANK YOU FOR TRYING OUR GAME <3 <3----------\n");
    getch();
}

