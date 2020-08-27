# README

In order to run this you must first run pip install Nba_api

# -+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-
# ----------------------FUNCTION DEFINTIONS------------------------
# -+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-

## 1) Get_Games_Ids():
 
This gets the current season's (2019-2020) Game ID numbers

It uses the leaguegamefinder from the Nba_api to build a dictionary

then it creates an empty list that it will iterate over with a for loop to fill said list

It returns a set to help eliminate duplicates
  

## 2) Find_Games_With_Threes(game):
This is the function that accesses the API and retrieves the game data.

Specifically the detailed PlaybyPlay data from Nba_api

It starts grabbing data in the form of dataframes

Then it uses regex in order to clean incoming string data from the playbyplay dataframe into a format that is usable

(I.E "a player made a shot" turns into JUMP_SHOT, with an accompanying value stored in EVENTMSGTYPE)

Then it loops over all of the play by play data, and assigns an accompanying EVENTMSGACTIONTYPE that is a more detailed value

Then a series of conditions are defined, specifially manipulating the data to answer the comeback threes question

A value num_of_threes is then calculated with all of these conditions/logic and added to the dataframe

And this function returns a DataFrame for analyis

#### EVENTMSGTYPE :
Simplified and cleaned broad event type description
#### EVENTMSGACTIONTYPE : 
More Detailed and cleaned event type description
#### three_pt_cond:
Condition ensuring that the shot is specifically a three pointer
#### made_shot_cond:
Condition ensuring that the shot is a make and not a miss
#### fourth_qtr_cond:
Condition ensuring that the plays captured are from the fourth quarter
#### PCTIMESTRING Lamda function: 
Ensures that the plays captured happened with at most 5 minutes remaining on the game clock
    
    
### Note: 
#### class EventMsgType(Enum):
is needed for the logic to compute

## 3) event_num_lookup(evt_num):

The values of EVENTMSGACTIONTYPE are converted from a number value to their descriptions and stored in a dictionary


# -+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-
# ------------------------------------LOGIC------------------------------------
# -+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-

Uses the defined functions to create a dictionary of games, keyed by their GAME_ID value

this dictionary then gets iterated over to create a final dataframe



## Determining is_comeback value


The SCOREMARGIN column gets cleaned and a simplified dataframe is created

Guarenteeing that the team is losing at the 5 minute mark


# Creation of a simplified final dataframe

A simplified dataframe is created for better analysis with three columns, Game_id, threes_under_five, is_comeback?





```python

```
