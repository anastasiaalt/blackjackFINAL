# blackjack

User Stories:
-What are my requirements?
-What should my app look like?

*No insurance offered at this blackjack table
*No split cards
*A win pays out 100%
*A blackjack plays out 150%

MONEY SECTION
Set a bank or house pot
Set each player purse
Set minimum bet


GAME LOGIC SECTION

**Begin game / shuffle function**

PROCESS FOR UPFRONT
X 1) Test if bank = 20*min bet --> assumption that 4 splits, 5 players, and dealer bust is worst possible outcome
--> Consulted with Sung, remove from game
X 2) Ask player to play
  If no, remove from game
  If yes, deduct minimum bet from player purse and ask next player
--> Consulted with Sung, remove from game
3) Give each player one unknown card and one known card beginning with dealer
--> Able to give each player two cards for now, will disguise later

3) Test for Dealer blackjack
If known card = A, test dealer hand value for a K,Q,J, and 10 --> 
  If dealer hand =!21, continue game
  If dealer hand = 21 && player hand =21, player keeps bet
    Else, take player bet
4) Test for player blackjack
If player hand = !21, continue game
If player hand = 21, pay player 150% of bet and return bet
--> DONE

PROCESS FOR EACH PLAYER
X 5) Test for split cards
If player hand has two cards same value, ask split yes or no
  If no, no action and step 6
  If yes, 1) deduct same bet amount again from player purse
          2) give two cards face down
          3) move to next player
---> Consulted with Sung, remove from now

6) Player can Hit (yes) or Stay (no) --> if no, to dealer
                                         if yes, test new hand value
                                            if >21, remove player and take bet
                                            if =21, automatic stay
                                            if <21, hit (yes) or stay (no)
                                                if no, next player
                                                if yes, test new hand value
                                                    if >21, remove player and take bet
                                                    if =21, automatic stay
                                                    if <21, ask player if she wants another card
//** this is going to be some kind of loop function to keep testing
//** need to include logic in this section for the value of A as 1 or 21... Thinking this is the last thing you test each time as a last resort basically to keep you alive and run the test again under the values 11 and 1... Could also do this as a card value for the A itself versus the hand....

Repeat #5 and #6 for all players

PROCESS FOR DEALER
7) Show dealer's second card and test value of dealer's hand
If dealer hand >= 16, compare player hand values
if hand < 16, add one card
      if new hand >21, pay all remaining players 100%
      if new hand >=16, compare all hand values
      if new hand < 16, add one card to dealer hand
            if new hand >21, pay all remaining players 100%
            if new hand >=16, compare all hand values
            if new hand < 16, add one card to dealer hand
//** this is going to be some kind of loop function to keep testing                                

8) Compare all hands
       if dealer hand > player hand, take player bet
       if dealer hand = player hand, return player bet
       if dealer hand < player hand, return player bet + pay 100% to player

9) Commit all transactions to bank and player purses
//This means the bank sits outside the game logic

9) Reset game
Return all cards to deck
Shuffle cards
Allow all players to participate again





Wire Frames:

Think about everything for the banking system of the game as one section
Think about everything for the logic or the winning of the game as another type of logic



PseudoCode

Will have an image or style for each of the cards
Four Seasons ~ Four Suits

Participants {P1,P2,P3,P4,P5,P6}
P1 = ()
P2 = ()
P3 = ()
P4 = ()
P5 = ()

Dealer = ()

Deck = {Winter, Spring, Summer,Fall}
Winter = {2,3,4,5,6,7,8,9,10,J,Q,K,A}
Spring = {2,3,4,5,6,7,8,9,10,J,Q,K,A}
Summer = {2,3,4,5,6,7,8,9,10,J,Q,K,A}
Fall = {2,3,4,5,6,7,8,9,10,J,Q,K,A}
---> 10/J/Q/K all programmed with the same logic as value 10
---> Programming ten types of cards with 13 different styles
---> Will need some sort of class for "hidden" that shows the back of the card / a generic card

The Ace!
//** need to include logic for the value of A as 1 or 11
--> Ace logic: x
               1) if A=1 && H>21 ---> Bust
               2) if A=1 && H=21 ---> Pay player 100%
               2) if A=11 && H=21 ---> Pay player 100%
               3)    
                  if A=1 && H<21 ---> Card? --> if No, next player
               3) if A=11 && H<21 ---> Card? --> if No, next player
               4) if yes,
                  if A=1 && H>21 --> Bust
                  if A=1 && H=21--> Pay player 100%
                  if A=11 && H=21--> Pay player 100%
                  if A=11 && H<21 --> Card? --> if No, next player
              5) if yes, repeat #4

Each player and dealer is going to be it's own section

Thinking you are going to keep player's hands as ULs and add LIs with the individual cards to them as an organizing structure

You add and remove these LIs with their values as you select options

Some kind of basic buttons where you declare "Hit" and "Stay" to add cards and pass to next player respectively

Do the whole bank as a section on the left, use the purse logic....



NEXT Steps:

1) Set up the DOM and get a basic HTML outline of the page
2) Make all the cards and the players
3) Make the bank
4) Work on the logic functions in Javascript / jQuery
