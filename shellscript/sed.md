# sed -> stream editor

# To delete a second line
  ```
  sed -e '2d' /etc/passwd
  ```
# To delete all line
  ```
  sed -e 'd' /etc/passwd
  ```
# For replace a word in a file
  ```
  sed "s/new_value/existing_value/" filename --> This will only change the output printing to screen not the actual file and it will only replace the first occurance
  s --> substitution

  sed "s/new_value/existing_value/g" filename  --> with "g" option it will replace all the matches
  sed -i "s/new_value/existing_value/g" filename  --> with -i it will chnage the actual file also
  ```
