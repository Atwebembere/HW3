# ReadMe

##1. A description of the project:

###The project seeks to determine if there is a relationship between pet preference among larks, owls and humming birds.
  
##2. A description of the dataset:

###The dataset comprises of a cohort of 29 Master of public health students in the Advanced data analysis class. Students recruited in the study are from a diverse background comprising of countries from different continents.
  
##3. A description of the code.

###a. Research question: Is there a pet preference among larks, owls and humming birds?

###b Variables considered: i) Pet_preference (like_cats; like_dogs) ii) larkORowl (lark, Owl, Hummingbird)

  #### Creating new categorical variable Preferred_pet:

C1survey <- C1survey %>% 
  mutate(Pet_preference = case_when (
    like_dogs == "Yes" & like_cats == "Yes" ~ "Both",
    like_dogs == "Yes" & like_cats == "No" ~ "Dogs",
    like_dogs == "No" & like_cats == "Yes" ~ "Cats",
                                     TRUE ~ "Neither") )

class(C1survey$Pet_preference) #checking variable type

####Next: create a table exploring both pet_preference and lark_owl_hummingbird 

contingency_table <- table(C1survey$Pet_preference, C1survey$larkORowl)
contingency_table #view the table to know the pet preferences

###Exporting dataset into CSV format file.

write.csv(C1survey, "C1survey_clea.csv", row.names = FALSE)
