# 신림중학교 파이썬 교육플랜

모든 수업 내용은 라이브 코딩 방식으로 진행할 예정입니다. 학생들은 진행멘토의 시범에 맞춰 코드를 입력하며, 다른 멘토가 이 과정을 보조합니다.

## 1차시: 파이썬 기본

목표

+ 구글 코랩에서 파이썬 코드를 입력하고 수행할 수 있다.
+ 정수/실수의 연산을 수행할 수 있다.
+ 조건문을 활용할 수 있다.
+ 반복문을 활용할 수 있다.
+ 함수를 만들 수 있다.
+ 리스트 원소에 접근할 수 있다.
+ 문자열 연산을 확인할 수 있다.

### 셋업

목표

+ 구글 코랩에서 파이썬 코드를 입력하고 수행할 수 있다.

### 죄수의 딜레마 시뮬레이터

출처: 컴퓨팅 기초 강의자료

목표

+ 정수/실수의 연산을 수행할 수 있다.
+ 조건문을 활용할 수 있다.
+ 반복문을 활용할 수 있다.
+ 함수를 만들 수 있다.

두 명의 사건 용의자가 체포되어 서로 다른 취조실에서 격리되어 심문을 받고 있다. 이들에게 자백여부에 따라 다음의 선택이 가능하다.  

![죄수의 딜레마 설명이미지](https://raw.githubusercontent.com/tenspoons-snucba/shms-22Spr/main/docs/prisoner.jpeg)  

+ 둘 중 하나가 배신하여 죄를 자백하면 자백한 사람은 즉시 풀어주고 나머지 한 명이 10년을 복역해야 한다.
+ 둘 모두 서로를 배신하여 죄를 자백하면 둘 모두 5년을 복역한다.
+ 둘 모두 죄를 자백하지 않으면 둘 모두 1년을 복역한다.

예시코드

```Python
DENY = 0
CONFESS = 1

from random import choice

def calculate_response_value(choice_a):
    choice_b = int(choice('01'))

    if choice_a == CONFESS:
        if choice_b == CONFESS:
            return 5
        else:
            return 0
    elif choice_a == DENY:
        if choice_b == CONFESS:
            return 10
        else:
            return 1
    else:
        # Erroneous Choice Handling should be developed further....
        return None
```

위의 코드를 활용해서, 어떤 참가자가 범죄를 숨기는 경우 복역 연수 평균을 구할 수 있다.

```Python
N = 10
sum = 0

for _ in range(N):
    sum += calculate_response_value(DENY)

average = sum / N
print(f"죄수 A가 부인하는 경우 평균값: {average:.3f}년")

```

### 인공지능 비서 만들기

출처: 컴퓨팅 기초 강의자료

목표

+ 리스트 원소에 접근할 수 있다.
+ 문자열 연산을 할 수 있다.
+ 패키지 포함 방법 및 사용 방법을 검색할 수 있다.

```Python
# Assume that given list today_covid_info has data as following
# Mentors crawl the webpage, and parse information for mentees as belows:
today_covid_info = ["83", "461", "240", "20084"]

from gtts import gTTS  # gTTS 모듈 임포트
from IPython.display import Audio  # Audio 모듈 임포트. colab에서 오디오 재생을 위해 필요

# fString으로 할 수 있지만, 문자열 연산을 연습하기 위해 "+"를 사용했어요.
message = "오늘의 코로나19 확진자 수는 " + today_covid_info[3] + "명이고, 사망자 수는 " + today_covid_info[0] + "명 입니다."

tts = gTTS(message, lang='ko')
tts.save('hello_ko.wav')
display(Audio('hello_ko.wav', autoplay=True))
```
