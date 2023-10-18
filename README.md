# Election-in-python
This code here is from my youtube video https://youtu.be/U6w-0w1pPu4?si=KMJGTij7WSqpIB7c  

# Project - Election
# The code should conduct election with any number of candidate and with any number of voters. Candidate Name should be
# given by user input and voter must name those who they want to vote for. The code should tell if there is a winner and
# the code should tell if the election was a tie, and between how many candidates.

# Function for names of candidates
def ask_for_names(group_num):
    candidate_names = []
    for i in range(group_num):
        while True:
            group_member = input(f"Please input candidate no.{i + 1}: ")
            # Error checking
            correct_name = True
            for j in group_member:
                if j.isalpha() or j.isspace():
                    pass
                else:
                    print("Invalid name.\n Enter correct name.")
                    correct_name = False
                    break
            if correct_name:
                break
            else:
                continue
        candidate_names.append(group_member)
    return candidate_names


def ask_for_votes(voter_num, *candidate_list):
    votes_list = []
    for i in range(candidate_num):
        votes_list.append(0)
    for i in range(voter_num):
        while True:
            candidate = input(f"Which candidate would you like to vote for, voter no.{i + 1}? ")
            if not (candidate in candidate_list):
                print("Enter correct name from the candidate list shown above.")
                continue
            else:
                break
        counter = 0
        for j in candidate_list:
            if j == candidate:
                votes_list[counter] += 1
            counter += 1
    return votes_list


# Asking for numbers of election part takers
candidate_num = int(input("How many candidates are there? "))
voters_num = int(input("How many voters are there? "))

# Asking for candidates names
candidate_list = ask_for_names(candidate_num)
print(candidate_list)

# Asking for votes from voters
votes_list = ask_for_votes(voters_num, *candidate_list)
print(f"{candidate_list} : {votes_list}")

max_vote = 0
for i in range(candidate_num):
    if votes_list[i] > max_vote:
        max_vote = votes_list[i]
counter = 0
while True:
    for i in range(candidate_num):
        if max_vote == votes_list[i]:
            counter += 1
            continue
        else:
            continue
    if counter > 1:
        print("This election was a tie!! \n Between: ", end='')
        for i in range(candidate_num):
            if max_vote == votes_list[i]:
                print(candidate_list[i] + " ", end='')
        break
    else:
        for i in range(candidate_num):
            if max_vote == votes_list[i]:
                print(f"The WINNER of this election is: {candidate_list[i]}!!!! Badahai ho!!\n")
                print("Namaste!!, aaj ke liye bas itna hi-")
                break
    break
