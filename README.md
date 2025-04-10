#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    int score = 0;
    int questionCount = 10;
    int difficulty;
    int min = 1, max = 10;
    int opCount = 2;

    printf("難易度を選んでください：\n");
    printf("1: かんたん\n");
    printf("2: ふつう\n");
    printf("3: むずかしい\n");
    printf("番号を入力: ");
    scanf("%d", &difficulty);

    switch (difficulty) {
        case 1: // かんたん
            min = 1; max = 9;
            opCount = 2;
            break;
        case 2: // ふつう
            min = 10; max = 99;
            opCount = 3; 
            break;
        case 3: // むずかしい
            min = 100; max = 999;
            opCount = 4; 
            break;
        default:
            printf("無効な難易度です。終了します。\n");
            return 1;
    }

    srand(time(NULL)); 

    for (int i = 0; i < questionCount; i++) {
        int a = rand() % (max - min + 1) + min;
        int b = rand() % (max - min + 1) + min;
        int op = rand() % opCount;
        int answer, userInput;

        switch (op) {
            case 0:
                printf("問題 %d: %d + %d = ?\n", i + 1, a, b);
                answer = a + b;
                break;
            case 1:
                printf("問題 %d: %d - %d = ?\n", i + 1, a, b);
                answer = a - b;
                break;
            case 2:
                printf("問題 %d: %d * %d = ?\n", i + 1, a, b);
                answer = a * b;
                break;
            case 3:
                a = a / b * b; 
                printf("問題 %d: %d / %d = ?\n", i + 1, a, b);
                answer = a / b;
                break;
        }

        printf("答えを入力: ");
        scanf("%d", &userInput);

        if (userInput == answer) {
            printf("正解！🎉\n");
            score++;
        } else {
            printf("不正解。正解は %d です。\n", answer);
        }

        printf("\n");
    }

    printf("ゲーム終了！あなたのスコアは %d / %d です。\n", score, questionCount);
    return 0;
}
