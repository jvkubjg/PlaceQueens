// Jakub Grzegorczyk
// PLacing queens 

import java.util.Scanner;
public class HW8_PlaceQueens {
    public static void main(String[] args) {
        Scanner kb = new Scanner(System.in);
        String option = "s";
        int repeat = 1;
        int size, row, column, count = 0; 
        
        char[][] board = new char[' '][' ']; // calling our main board 
        board[0][0] = '-'; // doing it so i can check letter if board is valid
        
        while(repeat == 1){ // output
            System.out.println("");
            System.out.println("q - quit \n" +
                               "r - reset, \n" +
                               "m - make, \n" +
                               "a - add queen, \n" +
                               "d - delete queen, \n" +
                               "c - count queen, \n" +
                               "p - print board");
           
          System.out.print("Enter option: "); 
          option = kb.next().toLowerCase(); // geting option 
          
          if(option.equals("r")){
              resetBoard(board); // reseting and printing 
              printBoard(board);
              
          }
          else if(option.equals("m")){ 
              System.out.println("Enter board size: "); // 
              size = kb.nextInt(); // taking input 
             
              board = createBoard(size); // making board
              printBoard(board);      // printing board
          }
          else if(option.equals("a")){
              System.out.println("Enter row and column: "); // taking input
              row = kb.nextInt();
              column = kb.nextInt();
              board = addQueen(board, row, column); // adding quen to board
              printBoard(board); // pritning everything 

          }
          else if(option.equals("d")){
              System.out.println("Enter row and column (1-N):"); // taking row and column
              
              row = kb.nextInt(); // taking row 
              column = kb.nextInt(); // taking column
              
              deleteQueen(board, row, column); // calling delete queens 
              redoStars(board); // calling method redoing stars
              printBoard(board); // calling printing board 
       
          }
          else if(option.equals("c")){
              countQueen(board);
          }
          else if(option.equals("p")){
              
              
              printBoard(board); // calling print board
          }
          else if(option.equals("q")){
              repeat = 999999;
          }
         
          else{
              System.out.println("");
          }
  
        }
        System.out.println("Good bye! ");
    }
    public static char[][] createBoard(int size){ // creating board methbod
        
        char[][] board = new char[size][size]; // giving size
        for(int i = 0; i < size; i++){
           for(int j = 0; j <size; j++){
               board[i][j] = ' '; // making array with spaces
           }
        }
        return board; // returnign board 
    }
    
    public static void printBoard(char[][] board){ // printing board method 
        if(board[0][0]=='-'){ // checking if the board is valid 
            System.out.println("Not a valid board. Cannot be printed.");
        }else{
        // making everyhing around boxes in array 
        String dashes = "";
        int size = board[0].length;
        for(int x = 0; x<(size*3) + 2 + size +1; x++){ // taking dashes
            dashes = dashes + "-";
        }
       
        System.out.print("  |");
        for(int i = 1; i <= size; i++){
            System.out.printf("%3d|", i);
        }System.out.println();
        System.out.println(dashes);
       
        for(int n = 0; n<size; n++){
            System.out.printf("%2d| ", n+1);
            for(int j = 0; j<size; j++){
               
               System.out.print(board[n][j]);
               System.out.print(" | ");
               
            }System.out.println("");
            System.out.println(dashes);
        }
        }
    }
    public static char[][] addQueen(char[][] board, int row, int column){ // adding queen method
        int length = board.length;
        if((length<row)||(length<column)||(column<0)||(row<0)){ // checking if input is valid
            System.out.println("Invalid row or column.");
        }else{
       row = row - 1;
       column = column -1; 
        board[row][column] = 'Q'; // making q a given place
       for(int i = 0; i < board[0].length; i++){ // first line 
           if (board[row][i] != 'Q'){
            board[row][i] = '*';
           }
       }
       for(int i = 0; i < board.length; i++){ // second line
           if (board[i][column] != 'Q'){
            board[i][column] = '*';
           }
       }
       int n = board.length;
       int row2 = row;
       int column2 = column;
             
        while((column2 != -1) && (row2 != -1)){ // crosses line
            if(board[row2][column2]!='Q'){
            board[row2][column2] = '*';
            }
            column2--;
            row2--;
        }
        
        int row1 = row;
        int column1 = column;
        
        while((column1 != n) && (row1 != n)){ // crosses line
            
            if(board[row1][column1] != 'Q'){
            board[row1][column1] = '*';
            }
            column1++;
            row1++;
        }
        int row3 = row;
        int column3 = column;
        
        while((column3 != -1) && (row3 != board.length)){ // crosses line 
            if(board[row3][column3] != 'Q'){
            board[row3][column3] = '*';
            }
            column3--;
            row3++;
        }
        int row4 = row;
        int column4 = column;
        
        while((row4 != -1) && (column4 != board.length)){ // crosses line
            if(board[row4][column4] != 'Q'){
            board[row4][column4] = '*';
            }
            column4++;
            row4--;
        }
        }
     return board;   
    }
    
    public static char[][] resetBoard(char[][] board){ // reseting board 
        if(board[0][0]=='-'){
            System.out.println("Not a valid board. Could not be reset.");
        }
        else{
            
        
        for(int i = 0; i<board.length; i++){ // giving spaces in each place 
            for (int j = 0; j<board.length; j++){
                board[i][j] = ' ';
            }
        }
        }
        return board;     
    }   
    public static void countQueen(char[][] board){ // counting queens 
        int count = 0;
        for(int i= 0; i<board.length; i++){ // if there is queen count ++
            for(int j = 0; j<board.length; j++){
                if(board[i][j] == 'Q'){
                    count++; 
                }
            }
        }
        if(count>0){ // printing result 
        System.out.printf("Counted queens on board: %d", count);
        System.out.println("");
        }else{
            System.out.println("Counter queens on board: 0");
        }
    }
    
    public static char[][] deleteQueen(char[][] board, int row, int column){ // deleting queen 
        if((board.length<row) || (board.length<column) || row<0 || column < 0){
            System.out.println("Invalid row or column");
        }else{
        
         row = row - 1;
       column = column -1;
       // the same code as in adding queen but instead of "*" we add " ";
       board[row][column] = ' '; 
       for(int i = 0; i < board[0].length; i++){ // deleting lines 
           if (board[row][i] != 'Q'){
            board[row][i] = ' '; // ading sapces 
           }
       }
       for(int i = 0; i < board.length; i++){ // deleting lines 
           if (board[i][column] != 'Q'){
            board[i][column] = ' '; // adding sapces
           }
       }
       int n = board.length;
       int row2 = row;
       int column2 = column;
             
         while((column2 != -1) && (row2 != -1)){ // 
            if(board[row2][column2]!='Q'){
            board[row2][column2] = ' '; // adding spaces 
            }
            column2--;
            row2--;
        }
        
        int row1 = row;
        int column1 = column;
        
        while((column1 != n) && (row1 != n)){ 
            
            if(board[row1][column1] != 'Q'){
            board[row1][column1] = ' '; // adding spaces 
            }
            column1++;
            row1++;
        }
        int row3 = row;
        int column3 = column;
        
        while((column3 != -1) && (row3 != board.length)){
            if(board[row3][column3] != 'Q'){ // if queen is on this position
            board[row3][column3] = ' '; // adding spaces 
            }
            column3--;
            row3++;
        }
        int row4 = row;
        int column4 = column;
        
        while((row4 != -1) && (column4 != board.length)){ 
            if(board[row4][column4] != 'Q'){ // 
            board[row4][column4] = ' '; // adding spaces 
            }
            column4++;
            row4--;
        }
       
        }
        return board;
    }

    public static char[][] redoStars(char[][] board){ // redoing stars 
        int row;
        int column;
        
        // the same code as add queens 
        // 
        
        for(row = 0; row<board.length; row++){ // 
            for(column =0; column<board.length; column++){
                if(board[row][column]=='Q'){
                    
        
       for(int i = 0; i < board[0].length; i++){
           if (board[row][i] != 'Q'){
            board[row][i] = '*';
           }
       }
       for(int i = 0; i < board.length; i++){
           if (board[i][column] != 'Q'){
            board[i][column] = '*';
           }
       }
       int n = board.length;
       int row2 = row;
       int column2 = column;
             
        while((column2 != -1) && (row2 != -1)){
            if(board[row2][column2]!='Q'){
            board[row2][column2] = '*';
            }
            column2--;
            row2--;
        }
        
        int row1 = row;
        int column1 = column;
        
        while((column1 != n) && (row1 != n)){
            
            if(board[row1][column1] != 'Q'){
            board[row1][column1] = '*';
            }
            column1++;
            row1++;
        }
        int row3 = row;
        int column3 = column;
        
        while((column3 != -1) && (row3 != board.length)){
            if(board[row3][column3] != 'Q'){
            board[row3][column3] = '*';
            }
            column3--;
            row3++;
        }
        int row4 = row;
        int column4 = column;
        
        while((row4 != -1) && (column4 != board.length)){
            if(board[row4][column4] != 'Q'){
            board[row4][column4] = '*';
            }
            column4++;
            row4--;
        }
                }
            }
        }

        return board; // returingn board 
    }

    
}
