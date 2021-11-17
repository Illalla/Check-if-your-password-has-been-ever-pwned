import requests
import hashlib
import sys

arg = sys.argv[1:]

def request(query_char):
    url = f'https://api.pwnedpasswords.com/range/{str(query_char)}'
    result = requests.get(url)
    if result.status_code != 200:
        raise RuntimeError
    return result


def le(resultt, tr):
    resli = (line.split(':') for line in resultt.text.splitlines())
    for x in resli:
        if x[0] == tr:
            if x[1] == '1':
                print(f'Your password has been used one time.')
                return
            else:
                print(f'Your password has been used {x[1]} times.')
                return 0
    print('Your password has never been used.')


def checker(password):
    sha1password = hashlib.sha1(password.encode('utf-8')).hexdigest().upper()
    frist5, therest = sha1password[:5], sha1password[5:]
    response = request(frist5)
    return le(response, therest)


def che(x):
    for i in arg:
        checker(i)

if __name__ == '__main__':
    sys.exit(che(arg))
