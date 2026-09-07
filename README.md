EX.NO.8 – BUILDING A SIMPLE COLLEGE ADMISSION CHATBOT
Aim

To design, implement, and test a simple rule-based chatbot in Python that answers frequently asked questions related to college admissions, including courses offered, eligibility criteria, fees, application process, required documents, important dates, hostel facilities, and contact details.

Introduction

A chatbot is a software application that simulates conversation with a human user, usually through text.

A rule-based chatbot works by comparing the user's input with predefined keywords or patterns and providing a suitable pre-written response. It does not require large training datasets or heavy computation, making it suitable for beginners learning the fundamentals of conversational AI.

In this experiment, a College Admission Chatbot is developed to work as a virtual help-desk assistant that provides instant answers to common admission-related questions.

Procedure
Step 1: Import Required Libraries

The required Python libraries are:

re: Used for regular expressions and searching keyword patterns in the user's message.
random: Used to randomly select one response when multiple responses are available for an intent.
import re
import random

Step 2: Design the Knowledge Base

The knowledge base is stored as a Python dictionary. Each key represents an intent, such as courses, eligibility, fees, hostel, or contact information.

Each intent contains:

Patterns: Keywords or phrases that may occur in the user's question.
Responses: Predefined answers that the chatbot can provide.

This structure makes the chatbot easy to extend because new admission topics can be added to the dictionary.

Example:

knowledge_base = {
    "courses": {
        "patterns": ["courses", "programs", "degrees"],
        "responses": [
            "We offer undergraduate and postgraduate courses."
        ]
    },
    "eligibility": {
        "patterns": ["eligibility", "qualification", "criteria"],
        "responses": [
            "Eligibility depends on the course you choose."
        ]
    }
}

Step 3: Match User Input to an Intent

The user's sentence is converted to lowercase so that matching is not case-sensitive.

The re.search() function searches for each pattern in every intent. If a pattern is found, the corresponding intent is returned. If no pattern matches, the function returns None.

def match_intent(message):
    message = message.lower()

    for intent, data in knowledge_base.items():
        for pattern in data["patterns"]:
            if re.search(pattern, message):
                return intent

    return None

Step 4: Generate the Chatbot Response

The get_response() function calls match_intent() to identify the user's intention.

If an intent is
