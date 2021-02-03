# CapstoneProject
import string
import random


def mid(s, x, y):
    return s[x-1:x+y-1]


def left(s, x):
    return s[:x]


def right(s, x):
    return s[-x:]


def onechar(s, num):
    num = num+1-2
    return s[num]


x = int(random.randint(1, 5))
y = int(random.randint(1, 5))
a = int(random.randint(1, 9))
b = int(random.randint(1, 9))
c = int(random.randint(1, 8))
d = int(random.randint(0, 9))
e = int(random.randint(0, 9))
N = 10
string = str(''.join(random.choice(string.ascii_letters + string.digits)
                     for _ in range(N)))
question = ["MID(" + string + ", " + str(x) + ", " + str(y) + ")",
            "LEFT(" + string + ", " + str(a) + ")",
            "RIGHT(" + string + ", " + str(b) + ")",
            "ONECHAR(" + string + ", " + str(c) + ")",
            "LENGTH(" + string + ")",
            "LCASE(" + string[d] + ")",
            "UCASE(" + string[e] + ")",
            "TO_UPPER(" + string + ")",
            "TO_LOWER(" + string + ")"]

answer = [mid(string, x, y), left(string, a), right(string, b),
          onechar(string, c), str(len(string)), string[d].lower(),
          string[e].upper(), string.upper(), string.lower()]
name = input("Enter your name:")
f = open("scorefile.txt", "w")
f.write(name + ":")
f.close()
score = 0
for i in range(0, 9, 1):
    x = input(question[i] + ":")
    if x == answer[i]:
        print("CORRECT!")
        score = score + 1
        f = open("scorefile.txt", "a")
        f.write(str(1) + ",")
        f.close()
    else:
        print("wrong it's " + str(answer[i]))
        f = open("scorefile.txt", "a")
        f.write(str(0) + ",")
        f.close()
f = open("scorefile.txt", "a")
f.write(str(score) + "/9")
f.close()
