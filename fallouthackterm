#!/bin/bash
echo "v9"

# Function to start a new game
start_new_game() {
  clear
  "$0"
  exit
}

# Function to generate random symbols
generate_symbols() {
  local symbols=""
  local symbols_list=("!" "@" "#" "$" "%" "^" "&" "*" "(" ")" "_" "-" "=" "+" "[" "{" "]" "}" "|" ":" ";" "\"" "," "<" "." ">" "/" "?" "\`" "~")

  for ((i = 0; i < 34; i++)); do
    symbols+=${symbols_list[RANDOM % ${#symbols_list[@]}]}
  done

  echo "$symbols"
}

# Function to calculate number of common characters between input and password

similarity_score() 
{
  local word1=$1
  local word2=$2
  local score=0

  for ((i = 0; i < ${#word1}; i++)); do
    if [[ ${word1:i:1} == ${word2:i:1} ]]; then
      ((score++))
    fi
  done

  echo "$score"
}

# Initialize RANDOM with the process ID
RANDOM=$$

# Arrays of words for each difficulty level
# Difficulty 1
difficulty_1_words=(
  "FRIED" "TREES" "RIGID" "HIRED" "TRIES" "WRITE" "TRIED" "GREED" "DRIED" "BRAIN" "SKIES" "LAWNS" "GHOST" "CAUSE" "PAINT" "SHINY" "MAKES" "GAINS" "THIEF" "BASES" "RAISE" "REFER" "CARES" "TAKEN" "WAKES" "WAVES" "WARNS" "SAVES"
)

# Difficulty 2
difficulty_2_words=(
  "STATING" "HEALING" "COSTING" "REASONS" "SEASIDE" "SPARING" "CAUSING" "CRAFTED" "PRISONS" "PRESENT" "DEALING" "SETTING" "LEAVING" "VERSION" "DEATHLY" "BLAZING" "GRANITE" "TESTING" "TRAITOR" "STAMINA" "TRINITY" "CALLING" "TALKING" "ACQUIRE" "WELCOME" "DECRIES" "FALLING" "PACKING" "ALLOWED" "SELLING" "AFFRONT" "WALKING"
)

# Difficulty 3
difficulty_3_words=(
  "CONQUORER" "CONSISTED" "WONDERFUL" "COMMITTEE" "SURRENDER" "SUBJECTED" "CONVICTED" "FORBIDDEN" "FORTIFIED" "COLLECTED" "CONTINUED" "PERIMETER" "SOUTHEAST" "RELEASING" "SOMETHING" "ACCEPTING" "MUTATIONS" "GATHERING" "LITERALLY" "REPAIRING" "INCESSANT" "INTERIORS" "REGARDING" "TELEPHONE" "OBTAINING" "EXTENSIVE" "DEFEATING" "REQUIRING" "UNLOCKING" "RECYCLING" "INSTINCTS" "BARTERING" "LEUTENANT" "COMMUNITY" "BATTERIES" "RECIEVING" "INCLUDING" "INITIALLY" "INVOLVING" "MOUNTAINS" "AUTHORITY" "CONFIDENT" "EXCELLENT" "INTEGRITY" "KNOWLEDGE" "MOTIVATED" "RESPECTED" "HONORABLE" "VISIONARY" "TENACIOUS" "PRINCIPLE" "HARMONIZE" "BRILLIANT" "THRIVING" "AMBITIOUS" "COURTEOUS" "EMPOWERED"
)

# Difficulty 4
difficulty_4_words=(
  "DISCOVERING" "ELIMINATING" "UNIMPORTANT" "MISTRUSTING" "MANUFACTURE" "RADIOACTIVE" "EXCLUSIVELY" "BOMBARDMENT" "DECEPTIVELY" "INDEPENDENT" "UNBELIEVERS" "EFFECTIVELY" "IMMEDIATELY" "INFESTATION" "DESCRIPTION" "INFORMATION" "REMEMBERING" "NIGHTVISION" "DESTRUCTION" "OVERLOOKING" "CONSISTENCY" "ENCOURAGING" "DISTRIBUTED" "ACKNOWLEDGE" "RECOGNITION" "CONFIGURING" "INVESTIGATE" "INTERACTING" "INFRASTRUCT" "PERSEVERING" "SIMPLIFYING" "RELIABILITY" "DEVELOPMENT" "APPLICATION" "ANONYMOUSLY" "AUTHORIZING" "CONFIDENCES" "DISCOVERIES" "ENGINEERING" "HARMONIZING" "INTERCHANGE" "LIMITATIONS" "PARALLELING" "RELIABILITY" "SIGNIFICANT" "TRANSMITTED" "UNDERSTANDS"
)

# Difficulty 5
difficulty_5_words=(
  "INFILTRATION" "ORGANIZATION" "SANGUINOLENCY" "SCHISMATIZING" "SYNECDOCHICAL" "TEMPESTUOUSLY" "TENUOUSNESSES" "THERMONUCLEAR" "TUSSICULATION" "UTRICULITISES" "UNVICARIOUSLY" "URBANIZATIONS" "VAPORIZATIONS" "VANQUISHMENTS" "VOICELESSNESS" "WEARABILITIES" "WHORISHNESSES" "WOODCRAFTSMAN" "XEROPHTHALMIA" "OBJECTIONABLY" "ONEIROCRITICS" "OVERWITHHOLDS" "NATIONALIZERS" "NARCOANALYSES" "NOSTALGICALLY" "NULLIFICATION" "MACROLECITHAL" "LALLAPALOOZAS" "LARKISHNESSES" "HABILIMENTARY" "FACILITATIONS" "FUSIBLENESSES" "FUROCOUMARINS" "EARNESTNESSES" "ELECTROCRATIC" "EIGENFUNCTION" "EMBELLISHMENT" "DAMAGEABILITY" "DECAPITALISED" "CAESAROPAPISM" "BACTERIOPHAGE" "BARBAROUSNESS" "AVICULTURISTS" "AXIOLOGICALLY" "AUTHORITARIAN" "AUTHORIZATION" "NOXIOUSNESSES" "KAKISTOCRACY" "KINAESTHESIA" "KLEPTOMANIAC" "MYTHOPOETIZE" "MALNUTRITION" "MULTIVOLTINE" "NARROWCASTED" "NARRATIVIZED" "OAFISHNESSES" "PHILOSOPHIZE" "POLARIMETERS" "QUALIFICATOR" "QUADRIENNIUM" "RACKETEERING" "RURALIZATION" "RUDDERFISHES" "UBIQUITOUSLY" "UNALIENATING" "VULCANIZABLE" "YAROVIZATION" "AUTHENTICITY" "APPRECIATION" "SPOKESPERSON" "LABORATORIES" "INITIATEHOOD" "SUBTERRANEAN" "PURIFICATION" "TRANSMISSION" "CIVILIZATION" "CONSTRUCTION" "RESURRECTION" "REPRIMANDING" "ACCOMPANYING" "OVERWHELMING" "CONVERSATION" "NORTHERNMOST" "TRANSCRIBING" "ANNOUNCEMENT" "SECLUSIONIST" "ABIRRITATION" "DIVERSIONARY" "HUMANITARIAN" "KINAESTHETIC" "LIQUEFACTION" "MISALIGNMENT" "MULTINOMINAL" "MERCIFULNESS" "PRACTICALISM" "PRASEODYMIUM" "RADIOTHORIUM" "SALUTATORIAN" "SCHIZOPHRENIC" "SALTATIONIST" "SYNOSTOTICAL" "THEOMORPHISM" "THIOXANTHENE" "TRADUCIANISM" "UNENUNCIABLE" "UXORIOUSNESS" "UNABJECTNESS" "VIGINTILLION" "VULCANIZABLE" "WAKERIFENESS" "WINTERBOURNE" "WHIPPOORWILL" "FISSIPALMATE" "FLABELLIFORM" "FELICITATION" "EXCOGITATIVE" "EDULCORATIVE" "EISTEDDFODIC" "DEVIATIONIST" "DOCUMENTABLE" "DICHLORBENIL" "CYCLANDELATE" "DISTOMACEOUS" "CALABRASELLA" "BALLADMONGER" "BLASTOCOELIC" "ALKALIZATION" "ALIMENTATIVE" "ADVANTAGEOUS" "ADSCITITIOUS" "ADMONISHMENT" "ABJECTEDNESS" "LOCALIZATION" "ZINCOGRAPHIC" "PLAUSIBILITY" "PIANISTICSES" "PHYTOPHTHORA" "PLEOMORPHISM" "QUINQUENNIAL" "RUTHLESSNESS" "SACCHARINITY" "NONACQUITTAL" "NEOANTHROPIC" "NUCLEOPHILIC"
)

# Prompt user to select difficulty
echo "SELECT TRAINING TERMINAL PROTOCOL LEVEL:"
echo "1. Very Easy [15]"
echo "2. Easy [25]"
echo "3. Average [50]"
echo "4. Hard [75]"
echo "5. Very Hard [100]"

# Read user input for difficulty choice
read -p "Enter the number corresponding to your difficulty choice: " difficulty

# Check if the input is a valid difficulty level
if ((difficulty >= 1 && difficulty <= 5 )); then
  # Set the words array based on the selected difficulty
  case $difficulty in
    1) words=("${difficulty_1_words[@]}");;
    2) words=("${difficulty_2_words[@]}");;
    3) words=("${difficulty_3_words[@]}");;
    4) words=("${difficulty_4_words[@]}");;
    5) words=("${difficulty_5_words[@]}");;
  esac
else
  # Default to difficulty 1 if an invalid input is entered
  words=("${difficulty_1_words[@]}")
fi
clear

# Generate a random password from the selected words
password=${words[RANDOM % ${#words[@]}]}

# Generate hack lines for the game
hack_lines=()
for ((i = 0; i < 19; i++)); do
  symbols1=$(generate_symbols)
  symbols2=$(generate_symbols)
  line="0xF$(printf "%03d" $((RANDOM % 1000)))   ${symbols1}   0xF$(printf "%03d" $((RANDOM % 1000)))   ${symbols2}"
  hack_lines+=("$line")
done

# Randomly choose a set number of hack lines from the generated hack lines
selected_hacklines=()
used_hacklines=()
for ((i = 0; i < 10; i++)); do
  # Randomly select a hack line
  index=$((RANDOM % ${#hack_lines[@]}))
  line="${hack_lines[$index]}"

  # Check if the hack line is already used
  while [[ "${used_hacklines[*]}" =~ $line ]]; do
    index=$((RANDOM % ${#hack_lines[@]}))
    line="${hack_lines[$index]}"
  done

  # Add the hack line to the selected hack lines and mark it as used
  selected_hacklines+=("$line")
  used_hacklines+=("$line")

  # Remove the hack line from the available hack lines
  unset "hack_lines[$index]"
done

# Generate the selected eight words
selected_words=()
while [[ ${#selected_words[@]} -lt 10 ]]; do
  word=${words[RANDOM % ${#words[@]}]}
  if [[ ! " ${selected_words[@]} " =~ " ${word} " ]]; then
    selected_words+=("$word")
  fi
done

# Concatenate the selected hack lines and the selected words
for ((i = 0; i < 10; i++)); do
  hack_line="${selected_hacklines[i]}"
  selected_word="${selected_words[i]}"
  position_choice=$((RANDOM % 2))

  if ((position_choice == 0)); then
    position1=$((RANDOM % 23 + 9))
    selected_hacklines[i]="${hack_line:0:position1}${selected_word}${hack_line:position1+${#selected_word}}"
  else
    position2=$((RANDOM % 23 + 55))
    selected_hacklines[i]="${hack_line:0:position2}${selected_word}${hack_line:position2+${#selected_word}}"
  fi
done

# Merge selected hack lines with remaining hack lines
remaining_hacklines=()
for line in "${hack_lines[@]}"; do
  if [[ -n "$line" ]]; then
    remaining_hacklines+=("$line")
  fi
done

# Combine selected hack lines and remaining hack lines
all_hacklines=("${selected_hacklines[@]}" "${remaining_hacklines[@]}")

# Randomize the order of elements in the all_hacklines array
mixed_hacklines=()
while [[ ${#all_hacklines[@]} -gt 0 ]]; do
  index=$((RANDOM % ${#all_hacklines[@]}))
  mixed_hacklines+=("${all_hacklines[index]}")
  unset "all_hacklines[index]"
  all_hacklines=("${all_hacklines[@]}")
done

# Check if the password is in the selected words
while [[ ! " ${selected_words[@]} " =~ " ${password} " ]]; do
  # Generate a new password from the selected words
  password=${words[RANDOM % ${#words[@]}]}
done

detected_duds=()

for line in "${mixed_hacklines[@]}"; do
  detected_pairs=()
  while [[ $line =~ (\([^\)]*\)|\[[^\]]*\]|\{[^\}]*\}|\<[^>]*\>|<>\(\)|\(\)|\[\]|\{\}) ]]; do
    opening_bracket="${BASH_REMATCH[1]}"
    content="${BASH_REMATCH[2]}"
    closing_bracket="${BASH_REMATCH[3]}"
    pair="$opening_bracket$content$closing_bracket"

    # Include brackets with no content
    if [[ -z "$content" ]]; then
      pair="$opening_bracket$closing_bracket"
    fi

    # Check if the pair contains any letters A-Z
    if ! echo "$pair" | grep -qP '[A-Z]'; then
      detected_duds+=("$pair")
    fi

    line="${line#*"${BASH_REMATCH[0]}"}"
  done
done

# Create a copy of detected_duds array
modified_duds=("${detected_duds[@]}")

# Remove first and last character from each entry in modified_duds using sed
for ((i = 0; i < ${#modified_duds[@]}; i++)); do
  modified_duds[$i]=$(echo "${modified_duds[$i]}" | sed 's/^.\(.*\).$/\1/')
done

nested_duds=()  # Initialize the nested_duds array

for pair in "${modified_duds[@]}"; do
  detected_pairs=()
  while [[ $pair =~ (\([^\)]*\)|\[[^\]]*\]|\{[^\}]*\}|\<[^>]*\>|<>\(\)|\(\)|\[\]|\{\}) ]]; do
    opening_bracket="${BASH_REMATCH[1]}"
    content="${BASH_REMATCH[2]}"
    closing_bracket="${BASH_REMATCH[3]}"
    current_pair="$opening_bracket$content$closing_bracket"

    # Include brackets with no content
    if [[ -z "$content" ]]; then
      current_pair="$opening_bracket$closing_bracket"
    fi

    nested_duds+=("$current_pair")  # Append the current_pair to nested_duds
    pair="${pair#*"${BASH_REMATCH[0]}"}"  # Remove the matched nested pair from the pair string
  done
done

# Create a copy of detected_duds array
modified_dudsL=("${detected_duds[@]}")

# Remove first character from each entry in modified_duds using sed
for ((i = 0; i < ${#modified_dudsL[@]}; i++)); do
  modified_dudsL[$i]=$(echo "${modified_dudsL[$i]}" | sed 's/^.\(.*\)$/\1/')
done

nested_dudsL=()  # Initialize the nested_duds array

for pair in "${modified_dudsL[@]}"; do
  detected_pairs=()
  while [[ $pair =~ (\([^\)]*\)|\[[^\]]*\]|\{[^\}]*\}|\<[^>]*\>|<>\(\)|\(\)|\[\]|\{\}) ]]; do
    opening_bracket="${BASH_REMATCH[1]}"
    content="${BASH_REMATCH[2]}"
    closing_bracket="${BASH_REMATCH[3]}"
    current_pair="$opening_bracket$content$closing_bracket"

    # Include brackets with no content
    if [[ -z "$content" ]]; then
      current_pair="$opening_bracket$closing_bracket"
    fi

    nested_dudsL+=("$current_pair")  # Append the current_pair to nested_duds
    pair="${pair#*"${BASH_REMATCH[0]}"}"  # Remove the matched nested pair from the pair string
  done
done

# Create a copy of detected_duds array
modified_dudsR=("${detected_duds[@]}")

# Remove last character from each entry in modified_duds using sed
for ((i = 0; i < ${#modified_dudsR[@]}; i++)); do
  modified_dudsR[$i]=$(echo "${modified_dudsR[$i]}" | sed 's/^\(.*\).$/\1/')
done

nested_dudsR=()  # Initialize the nested_duds array

for pair in "${modified_dudsR[@]}"; do
  detected_pairs=()
  while [[ $pair =~ (\([^\)]*\)|\[[^\]]*\]|\{[^\}]*\}|\<[^>]*\>|<>\(\)|\(\)|\[\]|\{\}) ]]; do
    opening_bracket="${BASH_REMATCH[1]}"
    content="${BASH_REMATCH[2]}"
    closing_bracket="${BASH_REMATCH[3]}"
    current_pair="$opening_bracket$content$closing_bracket"

    # Include brackets with no content
    if [[ -z "$content" ]]; then
      current_pair="$opening_bracket$closing_bracket"
    fi

    nested_dudsR+=("$current_pair")  # Append the current_pair to nested_duds
    pair="${pair#*"${BASH_REMATCH[0]}"}"  # Remove the matched nested pair from the pair string
  done
done

combined_duds=()
combined_duds+=("${detected_duds[@]}")
combined_duds+=("${nested_duds[@]}")
combined_duds+=("${nested_dudsL[@]}")
combined_duds+=("${nested_dudsR[@]}")

clear
# echo "Contents of 'combined_duds' array:"
# for element in "${combined_duds[@]}"; do
#   echo "$element"
# done
attempts=4
# Define the strings to display
strings=("ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
         "STATUS: POPULATING..."
         " "
         "$attempts ATTEMPT(S) LEFT: █ █ █ █"
         " ")

# Calculate the maximum length among all strings
max_length=0
for string in "${strings[@]}"; do
  if (( ${#string} > max_length )); then
    max_length=${#string}
  fi
done

# Loop through each character position
for ((i = 0; i < max_length; i++)); do
  clear
  # Loop through each string
  for string in "${strings[@]}"; do
    printf "%-${max_length}s\n" "${string:0:i+1}"
  done
  sleep 0.005
done

clear

# Display initial game information
echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
echo "STATUS: ENTER PASSWORD NOW"
# echo " "
# echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
echo " "
echo -n "$attempts ATTEMPT(S) LEFT: "
for ((i = 0; i < attempts; i++)); do
  echo -n "█ "
done
echo " "
echo " "

# Display the mixed hack lines
for line in "${mixed_hacklines[@]}"; do
  echo "$line"
  sleep 0.01
done

# Main game loop
previous_inputs=()
while [[ $attempts -gt 0 ]]; do
    # Read user input
    echo " "
    read -p "C> " input
    if [[ "$input" == "$password" ]]; then
        # Password entry
        sleep 1.5
        echo "> Entry accepted. Loading OS..."
        sleep 0.5
        # Ask if the user wants to try again
        echo " "
        read -p "RELOAD TERMINAL? (Y/N): " retry
        if [[ $retry =~ ^[Yy] ]]; then
            start_new_game
        else
            sleep 0.175
            echo " "
            echo "SHUTTING DOWN TERMINAL..."
            sleep 1
            exit
        fi
    elif [[ "${combined_duds[@]}" =~ "$input" ]]; then
        # Dud entry
        if [ $((RANDOM % 2)) -eq 0 ]; then
            ((attempts++))
        fi
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS: DUD DETECTED"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> DUD DETECTED."
        sleep 0.75
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS:"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> DUD DETECTED."
        sleep 0.25
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS: DUD DETECTED"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> DUD DETECTED."
        sleep 0.5
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS:"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> DUD DETECTED."
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS: DUD DETECTED"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
    elif [[ "${selected_words[@]}" =~ "$input" ]]; then
        # Denied entry
        ((attempts--))
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS: ENTRY DENIED"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> ENTRY DENIED. $(similarity_score "$input" "$password")/${#input}"
        sleep 0.5
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS:"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> ENTRY DENIED. $(similarity_score "$input" "$password")/${#input}"
        sleep 0.25
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS: ENTRY DENIED"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> ENTRY DENIED. $(similarity_score "$input" "$password")/${#input}"
        sleep 0.25
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS:"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> ENTRY DENIED. $(similarity_score "$input" "$password")/${#input}"
        sleep 0.25
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS: ENTRY DENIED"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        # Store the current input
        previous_inputs+=("$input")
        echo " "
        echo "C> $input"
        echo "> ENTRY DENIED. $(similarity_score "$input" "$password")/${#input}"
    else
        #Invalid entry
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS: INVALID ENTRY"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> INVALID ENTRY"
        sleep 0.5
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS:"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> INVALID ENTRY"
        sleep 0.25
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS: INVALID ENTRY"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> INVALID ENTRY"
        sleep 0.25
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS:"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
        echo " "
        echo "C> $input"
        echo "> INVALID ENTRY"
        sleep 0.25
        clear
        echo "ROBCO INDUSTRIES (TM) TERMLINK PROTOCOL"
        echo "STATUS: INVALID ENTRY"
        # echo " "
        # echo "DEV: $password, ${selected_words[@]}, ${combined_duds[@]}"
        echo " "
        echo -n "$attempts ATTEMPT(S) LEFT: "
        for ((i = 0; i < attempts; i++)); do
            echo -n "█ "
        done
        echo " "
        echo " "

        # Display the mixed hack lines
        for line in "${mixed_hacklines[@]}"; do
            echo "$line"
        done

        # Store and display previous attempts
        if [[ ${#previous_inputs[@]} -gt 0 ]]; then
            for stored_input in "${previous_inputs[@]}"; do
            echo " "
            echo "C> $stored_input"
            echo "> ENTRY DENIED. $(similarity_score "$stored_input" "$password")/${#stored_input}"
            done
        fi
    fi
done

if [[ $attempts -eq 0 ]]; then
  sleep 1
  echo " "
  echo "ACCESS DENIED."
  echo "PLEASE CONTACT AN ADMINISTRATOR."
  echo " "
  sleep 1
  echo "EXPECTED ENTRY: $password"
  echo " "
  sleep 1

  # Ask if the user wants to try again
  read -p "RELOAD TERMINAL? (Y/N): " retry
  if [[ $retry =~ ^[Yy] ]]; then
    start_new_game
  else
    sleep 0.175
    echo " "
    echo "SHUTTING DOWN TERMINAL..."
    sleep 2
    exit
  fi
fi
