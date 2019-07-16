# 문자열 함수 정의

### 문자열 비교 *strcmp*

```c
/* Delimit == '\0' */

int str_cmp (const char* str1, const char* str2) {
    int idx = 0;

    while (str1[idx] != DELIMIT) {
        if (str1[idx] != str2[idx]) break;

        idx ++;
    }

    return (str1[idx] - str2[idx]);
}
```

<br>

----

<br>

### 문자열 복사 *strcpy*

```c
/* Delimit == '\0' */

void str_copy (char* dest, const char* src) {

    while (*src != DELIMIT) {
        *dest = *src;
        dest ++;
        src ++;
    }

    *dest = DELIMIT;
}
```

<br>

------

<br>

### 문자열 길이 *strlen*

```c
/* Delimit == '\0' */

int str_len (const char* str) {
    int length = 0;

    while (*(str + length) != DELIMIT) {
        length ++;
    }

    return length;
}
```

<br>

------

<br>

### 문자열 변환 string to integer

```c
/* Delimit == '\0' */

int str_to_int (const char* str) {
    int value = 0;
    int is_negative = 0;

    // Remove White Space
    while (*str == ' ') str ++;


    // Check Negative Sign
    if (*str == '-') {
        is_negative = 1;
        str ++;
    }

    while (*str != DELIMIT) {
        if ('0' <= *str && *str <= '9') {
            value = (value * 10) + (*str - '0');
        }

        str ++;
    }

    if (is_negative) {
        value *= -1;
    }

    return value;
}
```

<br>

------

<br>

### 문자열 *reverse string*

```c
/* Delimit == '\0' */

char* reverse_str (char* str) {
    int length = str_len(str);
    int mid = length >> 1;

    for (int idx = 0; idx < mid; ++ idx) {
        swap(&str[idx], &str[length - 1 - idx]);
    }

    return str;
}
```

<br>