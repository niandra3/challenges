from collections import defaultdict
from random import choice

def markov_chain(words):
    # List words in 3-tuples
    grams = list(zip(words, words[1:], words[2:]))
    chain = defaultdict(list)
    # create Markov chain mapping 2-word prefix with a list of their 1-word suffix
    for w1, w2, w3 in grams[:-1]:
        chain[(w1, w2)].append(w3)
    return chain

def generate_text(chain, length):
    # always start random text with uppercase word
    text = [*choice([words for words in chain.keys() if words[0][0].isupper()])]
    for i in range(1, length):
        last = (text[i-1], text[i])
        text.append(choice(chain[last]))
    # end random text with '.' if possible
    if any('.' in word for words in chain.keys() for word in words):
        text.append(choice([words[1] for words in chain.keys() if words[1][-1] == '.']))
    return ' '.join(text)

def main():
    text = []
    with open('poe.txt', 'r') as f:
        text = [word for line in f for word in line.split()]
    chain = markov_chain(text)
    print(generate_text(chain, 500))

main()
