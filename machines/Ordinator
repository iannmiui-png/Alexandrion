import math

def S_orig(c):
    i = ord(c) - 65
    if i < 1:
        return (i, i+1)
    return (1, 9999)

def refine(word, radix):
    lo, hi = 0.0, float(radix)
    for c in word:
        a, b = S_orig(c)
        w = hi - lo
        lo = lo + w * (a / 9999)
        hi = lo + w * ((b - a) / 9999)
    return lo, hi

HEPT = "0ABCDEFGHIJKLMNOPQRSTUVWXYZ"

def to_heptavintimal(n):
    n = abs(n) % 19683
    if n == 0:
        return "0"
    digits = []
    while n > 0:
        n, r = divmod(n, 27)
        digits.append(HEPT[r])
    return "".join(reversed(digits))

def analyze(word):
    print("WORD:", word)
    print()

    last_hept = None

    # positive sweep: 19683 → 0
    for r in range(19683, -1, -1):
        lo, hi = refine(word, r)
        hept = to_heptavintimal(int(abs(lo)))
        if hept != last_hept:
            print(f"radix-{r}: {hept}")
            last_hept = hept

    # negative sweep: -1 → -99991
    for r in range(-1, -99992, -1):
        lo, hi = refine(word, r)
        hept = to_heptavintimal(int(abs(lo)))
        if hept != last_hept:
            print(f"radix-{r}: {hept}")
            last_hept = hept

analyze("!")
