Практична робота №3 Мануйленко Микола

    #include <stdio.h>

    int main() {
    int length; 
    scanf("%d", &length);

    long long dp_table[length + 1][2][2];

    dp_table[1][0][0] = 1;
    dp_table[1][1][0] = 1;

    for (int idx = 2; idx <= length; idx++) {
        dp_table[idx][0][0] = dp_table[idx][0][1] = 0;
        dp_table[idx][1][0] = dp_table[idx][1][1] = 0;
    }

    for (int idx = 2; idx <= length; idx++) {
        dp_table[idx][0][0] = dp_table[idx - 1][1][0] + dp_table[idx - 1][1][1];
        dp_table[idx][0][1] = dp_table[idx - 1][0][0];

        dp_table[idx][1][0] = dp_table[idx - 1][0][0] + dp_table[idx - 1][0][1];
        dp_table[idx][1][1] = dp_table[idx - 1][1][0];
    }

    long long total_count = dp_table[length][0][0] + dp_table[length][0][1] + dp_table[length][1][0] + dp_table[length][1][1];
    printf("%lld\n", total_count);

    return 0;
    }
