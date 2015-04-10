# pythonPrac
# Write a program to read through the mbox-short.txt and figure out who has the sent the 
# greatest number of mail messages. The program looks for 'From ' lines and takes the second 
# word of those lines as the person who sent the mail. The program creates a Python dictionary 
# that maps the sender's mail address to a count of the number of times they appear in the file. 
# After the dictionary is produced, the program reads through the dictionary using a maximum 
# loop to find the most prolific committer.

while(True):
    #Enter filename
    filename = raw_input("Enter file name (To quit type quit) ")
    if filename.lower() == 'quit':
        ans = raw_input(" Do you want to quit: ").lower()
        if ans == 'yes' or ans == 'y':
            break
        else:
            continue 
            
    # Handling user input for filename
    try:
        handle = open(filename)
    except:
        print "Bad file name"
        continue
        
    # Using the only sentences that start with From
    result = dict()
    reqwords = list()
    for line in handle:
        line.rstrip()
        if not line.startswith('From:') and line.startswith('From'):
            words = line.split()
            reqwords.append(words[1])
    
    #Inserting the values into the dictionary result
    for word in reqwords:
        result[word] = result.get(word,0) + 1    
        
            
    # finding the most common email address sent from with count
    bigcount = None
    bigword = None
    for word,count in result.items():
        if bigcount is None or count > bigcount:
            bigcount = count
            bigword = word
                
    print bigword,bigcount
    #break
