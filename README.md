import java.util.ArrayList;
public class HangManGame
{
    public static final int MAX_GUESSES = 6;
    private int wrongGuesses=0;
    ArrayList<Character> vowels = new ArrayList<Character>();
    ArrayList<Character>  consonants = new ArrayList<Character>();
    ArrayList<String>  sentences = new ArrayList<String>();
    private String sentence;
    private char a1 =' ';
    public HangManGame()
    {
    sentences.add("Patriots are the best");
    sentences.add("Bob isn't real!");
    sentences.add("Patriots should win the Super Bowl.");
    sentences.add("I love burritos!");
    sentences.add("Sleeping is very refreshing.");
    sentences.add("I love the Falcons.");
    sentences.add("Mr. Johnson is the best teacher!");
    sentences.add("Tompkins is a good school");
    sentences.add("I like to play football with my friends");
    sentences.add("Do you like to hangout with friends");
    this.sentence=sentences.get((int)(Math.random()*10));
    this.wrongGuesses=0;
    }
    
    public boolean won()
    {
    char a1=' ';
    int count=0;
    for (int x=0; x<sentence.length();x++)
    {
      
       if ((sentence.charAt(x) >='A' && sentence.charAt(x) <='Z') ||  (sentence.charAt(x) >='a' && sentence.charAt(x) <='z'))
       {
       a1 = sentence.charAt(x);
       a1= Character.toUpperCase(a1); 
       if(vowels.contains(a1) || consonants.contains(a1))
       ;
       else
       count++;
       }
       
    }
    if(count == 0 )
    return true;
    else 
    return false;
    }
    
    public int guessesLeft()
    {
    return MAX_GUESSES-wrongGuesses;
    }
    
    public void printSentence()
    {
    char a1=' ';
    System.out.print("\n");
    for (int x=0; x<sentence.length();x++)
    {
      
       if ((sentence.charAt(x) >='A' && sentence.charAt(x) <='Z') ||  (sentence.charAt(x) >='a' && sentence.charAt(x) <='z'))
       {
       a1 = sentence.charAt(x);
       a1= Character.toUpperCase(a1); 
       if(vowels.contains(a1) || consonants.contains(a1))
       System.out.print(sentence.charAt(x));
       else
       System.out.print("-");
       }
       else 
       System.out.print(sentence.charAt(x));
    }
    //printGuessed();
    }
    
     public void printHangMan()
    {
    System.out.print("\n\n\n\t\t|----------");
    System.out.print("\n\t\t|         |");
    System.out.print("\n\t\t|");
    if ((MAX_GUESSES-wrongGuesses) == 5)
    System.out.print("         O");
    if ((MAX_GUESSES-wrongGuesses) == 4)
    {
    System.out.print("         O");
    System.out.print("\n\t\t|        /");
    }
    if ((MAX_GUESSES-wrongGuesses) == 3)
    {
    System.out.print("         O");
    System.out.print("\n\t\t|       / |");
    }
    if ((MAX_GUESSES-wrongGuesses) == 2)
    {
    System.out.print("         O");
    System.out.print("\n\t\t|       / | \\");
    }
    if ((MAX_GUESSES-wrongGuesses) == 1)
    {
    System.out.print("         O");
    System.out.print("\n\t\t|       / | \\");
    System.out.print("\n\t\t|       /");
    }
    if ((MAX_GUESSES-wrongGuesses) == 0)
    {
    System.out.print("         O");
    System.out.print("\n\t\t|       / | \\");
    System.out.print("\n\t\t|       /  \\");
    }
    }
    
    public void printGuessed()
    {
    System.out.print("\n\n\nGuessed vowels: "+vowels);
    System.out.print("\nGuessed consonants: "+consonants);
    System.out.print("\nYou have "+(MAX_GUESSES-wrongGuesses)+" wrong guesses left.");
    printHangMan();
    }
    
    public boolean addGuesedLetter(char c)
    {
    c= Character.toUpperCase(c);    
    if(!(vowels.contains(c)) && !(consonants.contains(c)) && isInSentence(c) && !(isPunctuation(c)) && (c != ' '))
    {
    if(isVowel(c))
    vowels.add(c);
    else
    consonants.add(c);
    return true;
    }
    else
    {
        if (!isInSentence(c))
        {
            if(isVowel(c))
            {
            if (!(vowels.contains(c)))
            vowels.add(c);
            }
            
            else
            {
            if (!(consonants.contains(c)))
            consonants.add(c);
            }
        }
        
    wrongGuesses++;
    return false;
    
    }
    }
    
    public boolean isInSentence(char c)
    {
       if(sentence.toLowerCase().indexOf(c) >= 0 || sentence.toUpperCase().indexOf(c) >= 0)
       return true;
       else
       return false;
    }
    
    public boolean isPunctuation(char c)
    {
    if(c == '!' || c == ',' || c == '.' || c == '?' || c == ';' || c == ':' || c == '"' )
    return true;
    else
    return false;
    }
    
    public boolean isVowel(char c)
    {
    if(c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' || c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U')
    return true;
    else
    return false;
    }
}
