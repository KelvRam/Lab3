# Lab3
import java.util.ArrayList;
import java.util.Scanner;
class Question{
    private String question;
    private String answer;
    private int Difficulty;

    public Question(String newQuestion, String newAnswer, int newDifficulty){
        question = newQuestion;
        answer = newAnswer;
        Difficulty = newDifficulty;
    }

    public int getDifficulty() {
        return Difficulty;
    }public String getAnswer() {
        return answer;
    }public String getQuestion() {
        return question;
    }
    public void setAnswer(String answer) {
        this.answer = answer;
    }
    public void setQuestion(String question) {
        this.question = question;
    }
    public void setDifficulty(int difficulty) {
        Difficulty = difficulty;
    }
}


class Quiz {
    Scanner scan = new Scanner(System.in);
    String newQ;
    String newAns;
    String quizA;
    int remove;
    int diff;
    int Qnumb=1;
    int score;
    ArrayList<Question> Quest = new ArrayList<>();

    public void add_question() {
        System.out.println("What is the question Text?");
        newQ = scan.nextLine();
        System.out.println("What is the answer?");
        newAns = scan.nextLine();
        System.out.println("How Difficult (1-3)?");
        diff = scan.nextInt();
        scan.nextLine();
        Question Q = new Question(newQ, newAns, diff);
        Quest.add(Q);
        Qnumb += 1;
    }

    public void remove_question() {
        for (int i = 0; i < Quest.size(); i++) {
            System.out.println(i+1 + "."+ Quest.get(i).getQuestion());
        }
        System.out.println("Which question would you like to remove");
        remove = scan.nextInt();
        System.out.println();
        Quest.remove(remove);
        Qnumb -= 1;
    }

    public void modify_question() {
        for (int i = 0; i < Quest.size(); i++) {
            System.out.println(i +1 + "."+ Quest.get(i).getQuestion());
        }
        System.out.println("Which one to modify");
        remove = scan.nextInt();
        scan.nextLine();
        System.out.println("What is the new Question");
        newQ = scan.nextLine();
        System.out.println("What is the new Answer");
        newAns = scan.nextLine();
        System.out.println("What is the new difficulty");
        diff = scan.nextInt();
        scan.nextLine();
        Quest.remove(remove-1);
        Question Q = new Question(newQ, newAns, diff);
        Quest.add(Q);
    }

    public void give_quiz() {
        for (int i = 0; i < Quest.size(); i++) {
            Question Q = Quest.get(i);
            System.out.println(Q.getQuestion());
            quizA = scan.nextLine();
            if (quizA.equals(Quest.get(i).getAnswer())) {
                System.out.println("Correct!");
                score += 1;
            } else {
                System.out.println("Incorrect!");
            }
            if (score > -1) {
                System.out.println("You scored " + score + " points");
            }
        }
        }
    }



public class Lab3 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
Quiz newQuiz = new Quiz();
int choice = 10;
do {
    System.out.println("1. Add a question to the quiz\n" + "2. Remove a question from the quiz\n" +"3. Modify a question in the quiz\n" + "4. Take the quiz\n" + "5. Quit\n");
    choice=scan.nextInt();
if(choice==1){
    newQuiz.add_question();
}else if(choice ==2){
    newQuiz.remove_question();
}else if(choice ==3){
    newQuiz.modify_question();
}else if(choice==4){
    newQuiz.give_quiz();
}
}while(choice != 5);
    }
}
