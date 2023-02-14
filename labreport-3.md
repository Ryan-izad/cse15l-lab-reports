# Lab Report 3

## Command:`find`

**1. find . -name modifier**
  
*Example 1*
```
ryanizad@Ryans-MacBook-Pro-2 skill-demo1-data % find written_2 -name "Paris-WhatToDo.txt"
written_2/travel_guides/berlitz2/Paris-WhatToDo.txt
```
We can use the `-name` modifier here to recursively search written_2 for the file with the name "Paris_WhatToDo.txt", allowing us to search for a specific file.

*Example 2*
```
ryanizad@Ryans-MacBook-Pro-2 skill-demo1-data % find written_2 -name "*Bahamas*"
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Bahamas-Intro.txt
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt
```
In attaching the `*` character matching modifier to "Bahamas", we recursevly search written_2 for files that contain "Bahamas" anywhere in their name. 

Source[Link](https://chat.openai.com/chat)

**2. find . -type modifier

*Example 1*
```
ryanizad@Ryans-MacBook-Pro-2 skill-demo1-data % find written_2 -type d
written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Rybczynski
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Castro
written_2/travel_guides
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```
The `-type` modifier allows us to search for files of a specific type. In this case I used `-type d` to display all directory files in written_2

*Example 2*
```
ryanizad@Ryans-MacBook-Pro-2 skill-demo1-data % find written_2 -name "*berlitz*" -type d 
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```
We can use the `-type d` modifier in accordance with `-name` to find all directories with "berlitz" in their name.

Source[Link](https://chat.openai.com/chat)

**3. find . -exec modifier

*Example 1*
```
ryanizad@Ryans-MacBook-Pro-2 skill-demo1-data % find written_2 -type f -exec grep Lucayans {} \;
Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
```
Upon using the `-exec` modifier, we can execute the `grep` command on the found files to display the text of a file containing the word "Lucayans".

*Example 2*
```
ryanizad@Ryans-MacBook-Pro-2 skill-demo1-data % find written_2 -type f -exec grep Lucayans {} \; -exec rm {} \;
ryanizad@Ryans-MacBook-Pro-2 skill-demo1-data % grep -rl written_2 Lucayans                                    
grep: Lucayans: No such file or directory
```
We can use the `-exec` modifier here to execute a remove command on all files that contain the string "Lucayans". Upon trying to recursively search for the same file, we can see that it can no longer be found because it is deleted. 

Source[Link](https://chat.openai.com/chat)

**4. find . -ls modifier

*Example 1*
```
ryanizad@Ryans-MacBook-Pro-2 skill-demo1-data % find written_2 -name "*Bahamas*" -exec ls -l {} \;
-rwxr-xr-x  1 ryanizad  staff  73435 Feb 13 21:40 written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
-rwxr-xr-x  1 ryanizad  staff  9107 Feb 13 21:40 written_2/travel_guides/berlitz2/Bahamas-Intro.txt
-rwxr-xr-x  1 ryanizad  staff  19719 Feb 13 21:40 written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt
```
We can execute the `ls` command on files with the word "Bahamas" in their name to display each files information in long format. 

*Example 2*
```
ryanizad@Ryans-MacBook-Pro-2 skill-demo1-data % find written_2 -type d -exec ls -d {} \;
written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Rybczynski
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Castro
written_2/travel_guides
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```
We can execute the `ls -d` command on all files of the directory type to only list the names of the directory files. 

Source[Link](https://chat.openai.com/chat)
