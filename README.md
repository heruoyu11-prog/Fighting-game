# Fighting-game
#include <iostream>
#include <ctime>

using namespace std;

int main() {

    // seed rand + variables
    srand(time(0));
    string name;
    char readyToPlay;
    int roundNumber = 1;
    int playerAttack = 0;
    int botAttack = 0;
    int playerWins = 0;
    int botWins = 0;
    int attack;
    int successRate = 0;
   
    // intro
    cout << "Hello player, welcome to the game, enter your name: ";
    cin >> name;
    cout << "Hello " << name << "! Ready? Lets go!" << endl << endl;
   
    // rounds loop
    do {
       
        cout << "------- Round " << roundNumber << "! -------" << endl;
       
        // generate attack damage
        cout << "1) Punch (100% success rate, but less damage)" << endl;
        cout << "2) Short-distance swipe (higher damage, but less sucess rate)" << endl;
        cout << "3) Long-distance blast (50% success rate, but high damage)" << endl;
        cout << "Pick an attack: ";
        cin >> attack;
        cout << endl;
       
        switch (attack) {
            case 1:
                playerAttack = rand() % 10 + 1;
                cout << name << "'s attack damage: " << playerAttack << endl;
                botAttack = rand() % 20 + 1;
                cout << "Bot attack damage: " << botAttack << endl;
                break;
               
            case 2:
                playerAttack = rand() % 15 + 1;
                successRate = rand() % 101;
                if (successRate > 80) {
                    cout << "Miss!" << endl;
                    playerAttack = 0;
                }
                cout << name << "'s attack damage: " << playerAttack << endl;
                botAttack = rand() % 15 + 1;
                cout << "Bot attack damage: " << botAttack << endl;
                break;
               
            case 3:
                playerAttack = rand() % 20 + 1;
                successRate = rand() % 101;
                if (successRate > 50) {
                    cout << "Miss!" << endl;
                    playerAttack = 0;
                }
                cout << name << "'s attack damage: " << playerAttack << endl;
                botAttack = rand() % 10 + 1;
                cout << "Bot attack damage: " << botAttack << endl;
                break;
        }
       
        // compare attacks
        if (playerAttack > botAttack) {
            cout << name << " wins! Nice!" << endl << endl;
            playerWins++;
        } else if (botAttack > playerAttack) {
            cout << "Bot wins! Ouch, we'll get them next time!" << endl << endl;
            botWins++;
        } else {
            cout << "Draw!" << endl << endl;
        }
        roundNumber++;
    } while (roundNumber <= 5);    
   
    // game
    cout << "------- End of matches -------" << endl;
   
    // results
    if (playerWins > botWins) {
        cout << name << " wins! Good job, thanks for playing!";
    } else if (botWins > playerWins) {
        cout << "Bot wins! Nice try, thanks for playing!";
    } else {
        cout << "Draw! Thanks for playing!";
    }
}
