# Daily-Challenges--Day1
#TPRG-2131-01
#Nadim Gutto-100665657
#simplistic LCR calculator
'''This LCR calculator is ugly and incomplete. The code runs but doesn't actually
calculate anything. For full marks, you must complete the computation. You must
also "clean up" the code according to the course style guide and coding
standard. Specifically, you must:
  1) Take code that is duplicated and encapsulate it into a function that is
     called from the main program; the function must not "reach into" the
     main program for its working values;
  2) Rename variables so that they are not single letters, using descriptive
     names;
  3) Actually calculate the resonant frequency, bandwidth and Q factor for the
     SERIES resonant circuit (look up the formulas from ELEC II).
'''
import math #Imports math module from the Python library.


"""Get a positive float value from the user with a given prompt."""
def get_positive_input(prompt):
    
    value = float(input(prompt))#Takes the users input and converts it to a float.
    while value <= 0.0:#Checks if the value is less than or equal to 0.
        value = float(input("The value must be greater than zero\n" + prompt))#Prompts the user for a positive value.
    return value #Returns the Positive float value.

def calculate_resonant_frequency(inductance, capacitance):#Defines Function, takes two parameters.
    """Calculate resonant frequency for a series resonant circuit."""
    return 1 / (2 * math.pi * math.sqrt(inductance * capacitance))#Math formula for resonant frequency.

def calculate_bandwidth(resistance, inductance):#Defines Function, takes two parameters.
    """Calculate bandwidth for a series resonant circuit."""
    return resistance / inductance #Returns the bandwidth using the formula.

def calculate_q_factor(frequency, inductance, resistance):#Defines Function, takes three parameters.
    """Calculate Q factor for a series resonant circuit."""
    return frequency * inductance / resistance #Returns the Q-factor using the formula.

#Main Function
def main():
    print("Series resonant circuit calculator\n(CTRL-C to quit)") #Prints a message that this is a series resonant circuit.
    
    while True: #Loops the program until interupt (CTRL-C) is inputted.
        inductance = get_positive_input("What is the inductance in mH? ") / 1000  # Convert mH to H
        capacitance = get_positive_input("What is the capacitance in uF? ") / 1e6  # Convert uF to F
        resistance = get_positive_input("What is the resistance in ohms? ") #Prompts the user for resistor value in ohms.

        # Calculate the resonant frequency, bandwidth, and Q factor
        resonant_frequency = calculate_resonant_frequency(inductance, capacitance)#Gets the resonant frequency using the two perameter values.
        bandwidth = calculate_bandwidth(resistance, inductance)##Gets the bandwidth using the two perameter values.
        q_factor = calculate_q_factor(resonant_frequency, inductance, resistance)##Gets the Q-factor using the three perameter values.

        # Print the results
        print(f"\nResults for L = {inductance*1000} mH, C = {capacitance*1e6} uF, R = {resistance} ohms:")#Converts the value of "L" and "C" back to it's original units.
        print(f"Resonant Frequency: {resonant_frequency:.2f} Hz")#Prints the resonant frequency in Hertz (Hz) to two decimal places.
        print(f"Bandwidth: {bandwidth:.2f} Hz")#Prints the bandwidth in Hertz (Hz) to two decimal places.
        print(f"Q Factor: {q_factor:.2f}\n") #Prints Q-factor to two decimal places. 
        break #breaks out of the loop.
# Run the main function
main() #Calls and starts the functions program main().
