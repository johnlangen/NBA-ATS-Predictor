# NBA-ATS-Predictor
Regression based analysis algorithm resulting in a spread prediction for each night's NBA games. Employs Twitter API to automatically tweet every 24 hours

# Algorithm
  1) Create Regressions
     a) Regressions include all statistics from the SpreadPred2.csv
     b) These include: PTS, FGM, 3PA, 3P%, FTM, FTA, FT%, OR, DR, REB, AST, STL, BLK, TO, PF
     c) These statistics are then used in a linear regression against the teams ranking, to determine the importance of each statistic
     
  2) Regression Analysis / Main Algorithm
     a) From the regressions, we get a weighted sum for each team to be used in calculations
     b) All the matchups are then webscraped from Oddsshark.com, and their weighted sums are computed
     b) sum2 represents the weighted sum of the higher sum, sum1 represents the weighted sum of the lesser (sum2 > sum1)
     c) The final calculation is represented by: ((sum2+bias)-sum1)/18.8888 = FINALCALC (where 18.8888 is the constant, and here we use FINALCALC for that #)
     
  3) Final Analysis / Decision
     a) This is then compared against Vegas' spread for that matchup, which is also webscraped from Oddsshark
     b) Final analysis is done, which follows these rules
      * Assume the Grizzlies are playing the Celtics, where the Celtics are +2.5 by Vegas
      i) IF --> FINALCALC > Vegas' Spread (Ex. Grizzlies -3.5 > Grizzlies -2.5)
      ii) THEN --> Result = Celtics +2.5
      
      REASONING : The logic here is contradictive
        * The Grizzlies statistically should be favored by 1 more point
        * Vegas is decreasing the spread from that, which means there is some external reason affecting the team
        * Then you should take the Celtics, as the Grizzlies expected to play worse than they statistically are



        * * Using this logic, the program has thus far performed @ 62.87% over 237 games (Correct:149, Incorrect:88)
      


  
