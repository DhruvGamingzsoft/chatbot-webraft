# WebraftChatBot
The "chatbot-webraft" Python module is a powerful tool that allows users to create their own chatbots with custom datasets in an easy and efficient manner. 
It is designed to work with CSV datasets and provides a variety of model types to choose from, ensuring that users can select the best model for their specific needs. 
The module requires no high-end servers and can be used with or without training, making it a flexible and cost-effective solution for chatbot development. 
With the "chatbot-webraft" module, users can quickly and easily develop their own chatbots, customizing the dataset and model type to fit their specific requirements. 
Whether you're a beginner or an experienced developer, the "chatbot-webraft" module provides a simple and intuitive way to create custom chatbots with Python due to its easy to use syntax.

One of the best features of Chatbot-Webcraft is its ability to generate code scripts in specific programming languages from text. This means that you can use your preferred programming language, 
or even write your own code, and Chatbot-Webcraft will convert it into a script that is ready to use. Whether you are an experienced developer or just starting out, this feature makes it easy to 
build chatbots quickly and efficiently.

In summary, Chatbot-Webcraft is a must-have tool for anyone looking to create chatbots. With its wide range of features, including multiple model types, easy customization, and code generation capabilities,
Chatbot-Webcraft is the perfect tool for anyone looking to build chatbots with ease and efficiency.

**PLEASE NOTE THAT THIS MODULE IS IN BETA AND CHATBOTS CREATED WITH IT MAY RESPOND WITH UNEXPECTED ANSWERS**

### **USAGE:**
#### Import library
```from chatbot_webraft import chatbot```

##### Create Model
```chatbot.create_model("my-model")```

##### Load  CSV DATASET (here 'input' needs to be replaced with the column in dataset that has the fields containing the data to be inputted same to be done with 'label' but with fields containing the data to be outputted. )
```chatbot.dataset(CSV_FILE_NAME,'input','label',"my-model"") ```

##### Add more data to chatbot(OPTIONAL)
```chatbot.add_data("my-model"",["input1","input2"],["output1","output2"]) ```

##### Specify Input
```input = "hi"``` / ```input = input("Enter: ")```
##### Run chatbot (for default set MODEL_TYPE to "spimx")
```print(chatbot.model_load(MDDEL_TYPE,input,"my-model"))```/```chatbot.model_load(MDDEL_TYPE,input,"my-model")``` 
##### Use codewriter (currently python supported)
```print(codewriter("python",input,"my-model")``` / ```chatbot.model_load("pywriter",input,"my-model")```

### **Model Types:**
Inbuilt model types: spimx (best), spimxr (better), spim (good), rasv (not that good)
You can use other model types by downloading them from [here]("https://models.chatbot.webraft.in") and define path where modeltype (.wrmodel) file is stored to MODEL_TYPE

### **Basic BOT Usage:**
 ```
 #Import library
from chatbot_webraft import chatbot

#set model name
model = "my-model" 

#create model
chatbot.create_model(model)

#load CSV dataset , Mention input column (question) and label column (answer)
chatbot.dataset(CSV_FILE_NAME,INPUT_COLUMN,LABEL_COLUMN,model) 


#run in loop
while True:
  prompt = input("You: ")    
  #run model and parse input
  print("Bot: ",chatbot.model_load("spimx",prompt,model)) 

 ```

 ### **Bot usage for discord:**
```
#Import libraries
from chatbot_webraft import chatbot
import discord 
client = discord.Client(intents=discord.Intents.all())


model = "my-model" #set model name
chatbot.create_model(model) #create model
chatbot.dataset(CSV_FILE_NAME,INPUT_COLUMN,LABEL_COLUMN,model) #load CSV dataset .. Mention input column (question) and label column (answer)
chatbot.add_data(model,["hey","what about you"],["hello bro","im fine ,you?"]) #add more data to model (Not saved , only in memory). Data that you may want to add later.
@client.event
async def on_message(message):
    if message.author == client.user:
        return

    prompt = message.content
    
    await message.reply(chatbot.model_load("spimx",prompt,model)) #run model and parse output
client.run(BOT_TOKEN)
```
### **Basic codewriter usage:**
```
 #Import library
from chatbot_webraft import chatbot

#set model name
model = "my-model" 

#create model
chatbot.create_model(model)

#load CSV dataset , Mention input column (question) and label column (answer)
chatbot.dataset(CSV_FILE_NAME,INPUT_COLUMN,LABEL_COLUMN,model) 


#run in loop
while True:
  prompt = input("You: ")    
  #run model and parse input
  print("Bot: ",chatbot.model_load("pywriter",prompt,model)) #Or codewriter("python",prompt,model)
```

### **SAMPLE CSV DATASET:**
Download Sample csv dataset from [here]("https://webraft.in/sample.csv") , Dont forget to put the file in your project directory
Change `CSV_FILE_NAME` to "sample.csv" , `INPUT_COLUMN` to "input" , `LABEL_COLUMN` to "label" in the code

### **Errors:**
Error 1 - This error indicates that the model name used in specific function is not same as the modelname set with chatbot.createmodel() 
Error 2 - This error indicates that the codewriter couldn't convert specific text to code due to lack of resources 
Error 3 - This error indicates that the file being set in any of these functions: chatbot.dataset() , chatbot.model_load() doesn't exist 