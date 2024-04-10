# Reveal-Cards-In-Increasing-Order
You are given an integer array deck. There is a deck of cards where every card has a unique integer. The integer on the ith card is deck[i].  You can order the deck in any order you want. Initially, all the cards start face down (unrevealed) in one deck.

class Solution:
    def deckRevealedIncreasing(self, deck: List[int]) -> List[int]:
        deck.sort()
        
        n = len(deck)
        result = [0] * n
        indices = deque(range(n))
        
        for card in deck:
            idx = indices.popleft()  
            result[idx] = card       
            if indices:               
                indices.append(indices.popleft())  
        
        return result
