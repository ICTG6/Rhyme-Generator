# Table of Contents
	1. Introduction
	2. Set up
	3. Further Work 
	4. Resources 
	
	
# 1. Introduction
	This is our first group project together, we chose to work on "Rhyme Generator". Nowadays there are different hobbies and one of those is writing lyrics and poems. This topic picked our interest on how rhyme works. Rhymes help people to express themselves in a creative way. Our target of current project is to help user in finding rhymes based on user input word and will result a list of word that rhymes with the user input.
	There are a lot of rhymes pattern and our project right now will only focus on the ABAB pattern where first line will rhyme with the third line and the second line will rhyme with the fourth line, vice versa. For Example: 
		I've been reading books of old
		The legends and the myths
		The testaments they told
		The moon and its eclipse
	Artist: The Chainsmokers and Coldplay 
	Song: Something Just Like This

	We started our project by doing a web scrapping using Python to get csv file with the content of some rhymes word and then will do some more code to get user input and give out the list of word that rhymes with the user input 

	We will be using Natural Language Toolkit (NLTK) Library to do our rhyme generator project. The Notebook includes four parts of code:
	1.  Load the NLTK Library
	2.  Generate Rhyme
	3.  Differentiate Rhyme 
	4.  Get user Input



# 2.Set Up

## 2.1. Load Library
	Download The NLTK Library inside local PC first then run this code
		import nltk
		nltk.download('cmudict')

## 2.2. Code to Generate the Rhyme
Check words

	def check(word1, word2):
	  if(word1==word2):
 	   return True

Get the libraries Content

	entries = nltk.corpus.cmudict.entries()
	print(entries)

	def rhyme(inpword, stress):
    	entries = nltk.corpus.cmudict.entries()

get the syllabus

   	 Num_of_syl = [(input_word, syl) for input_word, syl in entries if check(input_word,inpword)]
   	 listOfRhymes = []

get the word which have the same end as the syllabus

   	 for (input_word, syllable) in Num_of_syl:
             listOfRhymes += [input_word for input_word, Pronunciation in entries if (check(Pronunciation[-stress:],syllable[-stress:]))]      
    	 return set(listOfRhymes)



## 2.3. Code to Differentiate a Rhyme

	def RhymeorNot(firstword, secondword):
    		if firstword.find(secondword) == len(firstword) - len(secondword):
     		   return False
    		if secondword.find(firstword) == len(secondword) - len(firstword): 
     		   return False

    	return firstword in rhyme(secondword, 1)

## 2.4. Get User Input
This code will get user input and output a list of rhymes words based on the input
	
		a = str(input('Enter word:'))
		b = int(input('Enter Level of how good the rhyme is:'))
		userinput = rhyme(a,b)
		print(userinput)


 This code will be used to check is a word rhymes with the 2 given inputs.
	
		RhymeorNot('near','dear')


# 3. Further work
 	Our target of this project is the set up a website where people could use it to search for a rhyme of a words. We have another goal to improve our current project where instead of giving a result of a list of rhymes word based on user input, we wanted to develop it into a generator that could give output of one line that rhymes with the specific words so there will be an AI that could create and generate the one line automatically.
	Another future development that we wanted to make after the target before is achieved is to developed the AI to be able to generate a whole poem by itself by taking a view keywords as an identifier on the topic and words that wanted to be used in the Poem/Lyrics.

# 4. Resources
	These are some resources we use to develop our rhyme generator project: 
	
		o https://www.rhymedb.com/ 
		o https://stackoverflow.com/questions/25714531/find-rhyme-using-nltk-in-python
		o https://www.nltk.org/data.html 

