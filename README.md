## Design and Implementation of LangChain Expression Language (LCEL) Expressions

## DEVELOPED BY: SREEVALSAN 
## REGISTER NUMBER:212223240158

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:
We need to create a LangChain Expression Language (LCEL) expression that processes two input parameters, generates a response using a language model, and outputs a structured format based on a defined schema. The implementation should involve a prompt, model, and output parser to handle the input and generate a response effectively.


### DESIGN STEPS:

#### STEP 1:
Define a prompt template that includes the input parameters (e.g., topic and context). The prompt should guide the model in generating a summary and key points from the provided context.

#### STEP 2:
Initialize a language model (e.g., OpenAI’s text-davinci-003) that will generate the output based on the prompt template. Set a temperature parameter for controlling response creativity.

#### STEP 3:
Define the output structure by creating a response schema with multiple fields (e.g., summary and key_points). Use the structured output parser to extract the relevant information from the model's response.

### PROGRAM:
```py
from langchain.prompts import PromptTemplate
from langchain.llms import OpenAI
from langchain.output_parsers import StructuredOutputParser, ResponseSchema

prompt = PromptTemplate(
    input_variables=["topic", "context"],
    template="Write a summary about {topic} based on the following context: {context}"
)

llm = OpenAI(model="text-davinci-003", temperature=0.7)

response_schemas = [
    ResponseSchema(name="summary", description="A concise summary of the topic"),
    ResponseSchema(name="key_points", description="Main points covered in the summary")
]

output_parser = StructuredOutputParser.from_response_schemas(response_schemas)

def evaluate_expression(topic, context):
    formatted_prompt = prompt.format(topic=topic, context=context)
    raw_output = llm(formatted_prompt)
    parsed_output = output_parser.parse(raw_output)
    return parsed_output

if __name__ == "__main__":
    topic = "Artificial Intelligence"
    context = "Artificial Intelligence is a field of study focusing on creating machines capable of mimicking human intelligence. It includes machine learning, robotics, and natural language processing."
    result = evaluate_expression(topic, context)
    print("LCEL Expression Output:")
    print(result)
```

### OUTPUT:

### RESULT:
The system successfully processes the input parameters, generates a summary, and extracts key points from the context provided. This demonstrates the functionality of LangChain Expression Language (LCEL) expressions, utilizing a prompt, language model, and output parser to produce structured responses.
