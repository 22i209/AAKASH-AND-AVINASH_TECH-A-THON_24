# ITA-Hackathon-24
This is a mental health chatbot that provides the user with breathing exercises , quotes and mental health tips based on the user's mood.

**Natural Language Processing (NLP) was used through:**

1. Keyword Matching
The chatbot uses basic keyword matching to determine the user's intent. This is a rudimentary form of NLP. The chatbot looks for specific keywords or phrases in the user input to decide how to respond. For example:

"sad" triggers a response related to sadness.
"quote" triggers a response with a motivational quote.
"breathe" triggers instructions for a breathing exercise.

2. Case Insensitivity
To make keyword matching more robust, the input is converted to lowercase using input.toLowerCase(). This ensures that the bot can correctly match keywords regardless of how the user capitalizes them.

3. Response Generation
Based on the identified keywords, the chatbot generates predefined responses. This is a basic form of response generation where the chatbot selects an appropriate response from a set of options based on the user's input.



**Source Code:**


package hackathon;

import javax.swing.*;

import java.awt.event.ActionEvent;

import java.awt.event.ActionListener;

public class Bot extends JFrame {

    private JTextArea ChatArea = new JTextArea();
    private JTextField ChatBot = new JTextField();

    public Bot() {
        JFrame frame = new JFrame();
        frame.setDefaultCloseOperation(EXIT_ON_CLOSE);
        frame.setResizable(true);
        frame.setVisible(true);
        frame.setLayout(null);
        frame.setSize(500,500);
        frame.setTitle("Mental Health ChatBot");
        frame.add(ChatArea);
        frame.add(ChatBot);
        ChatArea.setSize(600, 400);
        ChatArea.setLocation(2, 2);
        ChatBot.setSize(600, 30);
        ChatBot.setLocation(2, 400);
        ChatArea.append("How are you feeling today? Happy, sad, tired, or do you need help?\n");

        ChatBot.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String userInput = ChatBot.getText();
                ChatArea.append("You: " + userInput + "\n");

                String response = bot(userInput); // Generate the bot response based on user input
                botResponse(response); // Display the response

                ChatBot.setText(""); // Clear the input field after sending
            }
        });
    }

    private String bot(String input) {
        input = input.toLowerCase(); // Make the input case-insensitive

        if (input.contains("sad")) {
            return "I'm sorry to hear that you're feeling sad. Would you like breathing exercises, quotes, or tips?";
        } else if (input.contains("happy")) {
            return "I'm glad to hear that you're feeling happy! Would you like breathing exercises, quotes, or tips?";
        } else if (input.contains("help")) {
            return "I'm here to help. Would you like breathing exercises, quotes, or tips?";
        } else if (input.contains("tired")) {
            return "It's okay to feel tired. Make sure to take some time to rest and recharge. Would you like breathing exercises, quotes, or tips?";
        } else if (input.contains("quote")) {
            return getMotivationalQuote();
        } else if (input.contains("breathe")) {
            return getBreathingExercise();
        } else if (input.contains("tips")) {
            return getMentalHealthTips();
        } else {
            return "I'm here to chat if you need anything!";
        }
    }

    private String getMotivationalQuote() {
        // Return a motivational quote
        return "Here's a motivational quote for you: 'The only way to do great work is to love what you do.' — Steve Jobs";
    }

    private String getBreathingExercise() {
        // Provide instructions for a breathing exercise
        return "Try this 4-7-8 breathing exercise: Breathe in quietly through your nose for a count of 4, hold your breath for a count of 7, and exhale completely through your mouth for a count of 8. Repeat 4 times.";
    }

    private String getMentalHealthTips() {
        // Provide mental health tips
        return "Here are some mental health tips: 1) Stay connected with loved ones. 2) Practice mindfulness and relaxation techniques. 3) Engage in regular physical activity. 4) Seek professional help if needed.";
    }

    private void botResponse(String response) {
        ChatArea.append("Bot: " + response + "\n");
    }

    public static void main(String[] args) {
        new Bot();
    }
}
