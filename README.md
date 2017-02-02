# tado_API_python
small python scripts that accesses tado smart thermostat
I would like to add a great deal of thanks to Stephen Phillips, that engineered the tado API and documented the V2 API blog. 
I translated that API into simple usable python scripts, in order to use it freely with other automated tasks

Usage is simple; 
There are three files: tado_set_heating, tado_set_auto and tado_get_token; 
The last one, tado_get_token contains the API to get, check and renew the required authentication token based on user/pass; 
The token is then saved in the same directory as the python scripts, in order to be checked everytime is required. I used this method because 
the script itself shouldn't be dependent on a stored variable, it should be called by any app, with the temp parameter, if the token extracted 
is valid, then the command is executed, or if is not valid, because the token expired yesterday, then refresh the token and store it in the file.

tado_set_heating accepts one float temperature argument in line with the script as :
dodo:~ python tado_set_heating.py 21.3 
The input is rounded to 2 decimals then checked to be within thermostat temp range from 5 ~ 26 degrees, higher values are not accepted;
If this is true, then the thermostat is set in manual mode with the new given temperature setting; 

tado_set_auto it disables the manual override of the thermostat, canceling the above manual setting and allowing tado to calculate 
independently it's temperature, based on schedule, weather and so on. 
