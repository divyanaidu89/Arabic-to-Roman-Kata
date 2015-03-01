//Arabic-to-Roman-Kata
package arabictoroman;
import java.util.Scanner;
public class ArabicToRoman {

	public static void main(String[] argrs) {
		
            @SuppressWarnings("UnusedAssignment")//Conversion from Arabic to Roman
		int loopExit = 0;
		do{
		System.out.println("Please enter Arabic(1-3000) number to get converted to Roman");
		Scanner sc = new Scanner(System.in);
		int arabicNumber = sc.nextInt();
		StringBuffer romanNumber = new StringBuffer("");
	    while(arabicNumber < 1 || arabicNumber > 3000){
	        System.out.println("The arabic number value should be between 1-3000. Please enter again");
	        arabicNumber = sc.nextInt();
		}
	    int I = 1;
	    int V = 5;
	    int X = 10;
	    int L = 50;
	    int C = 100;
	    int D = 500;
	    int M = 1000;
	    
	    
	    while (arabicNumber != 0){ // for numbers more tham 1000
		    if(arabicNumber >= 1000) {
		        romanNumber.append("M");
		        arabicNumber = arabicNumber - M;
		    }
		    else if (arabicNumber >= 900) {
		        romanNumber.append("CM");
		        arabicNumber = arabicNumber - (M-C);
		    }
		    else if (arabicNumber >= 500) { //handles 800, 700, 600, 500
		        romanNumber.append("D");
		        arabicNumber = arabicNumber - D;
		    }
		    else if (arabicNumber >= 400) {
		        romanNumber.append("CD");
		        arabicNumber = arabicNumber - (D-C);
		    }
		    else if (arabicNumber >= 100) {//handles 300, 200, 100
		        romanNumber.append("C");
		        arabicNumber = arabicNumber - C;
		    }
		    else if (arabicNumber >= 90) {
		        romanNumber.append("XC");
		        arabicNumber = arabicNumber - (C-X);
		    }
		    else if (arabicNumber >= 50) {//handles 80, 70, 60, 50
		        romanNumber.append("L");
		        arabicNumber = arabicNumber - L;
		    }
		    else if (arabicNumber >= 40) {
		        romanNumber.append("XL");
		        arabicNumber = arabicNumber - (L-X);
		    }
		    else if (arabicNumber >= 10) {//handles 30, 20, 10
		        romanNumber.append("X");
		        arabicNumber = arabicNumber - X;
		    }
		    else if (arabicNumber >= 9) {
		        romanNumber.append("IX");
		        arabicNumber = arabicNumber - (X-I);
		    }
		    else if (arabicNumber >= 5) {//handles 8, 7, 6, 5
		        romanNumber.append("V");
		        arabicNumber = arabicNumber - V;
		    }
		    else if (arabicNumber >= 4) {
		        romanNumber.append("IV");
		        arabicNumber = arabicNumber - (V-I);
		    }
		    else if (arabicNumber >= 1) {//handles 3, 2, 1
		        romanNumber.append("I");
		        arabicNumber = arabicNumber - I;
		    }    
	    }
	    
	    //Conversion from Roman Numbers to Arabic
	    System.out.println("Roman number is: "+romanNumber);
	    	    
	    System.out.println("Please enter Roman(I-MMM) enter to get converted to arabic");
		Scanner sc1 = new Scanner(System.in);
		String romanNum = sc1.next();
		int index = 0;
		int number = 0;
		char nextchar;
		while(index <= romanNum.length()-1){
			//Will be checking the next index only if the roman value is either I ,V, C.Depending on that we will be deciding either to add directly the roman value or do the substraction. for others directly add the roman value
			if(romanNum.charAt(index) == 'I'){
				if(index == romanNum.length()-1){
					number += 1;
					index = index+1;
				}
				else{
					nextchar = romanNum.charAt(index+1);
					if(nextchar == 'V'){
						number += 4;
						index = index+2;
					}
					else if(nextchar == 'X'){
						number += 9;
						index = index+2;
					}
					else{
						number += 1;
						index = index+1;
					}
				}
			}
			else if(romanNum.charAt(index) == 'X'){
				if(index == romanNum.length()-1){
					number += 10;
					index = index+1;
				}
				else{
					nextchar = romanNum.charAt(index+1);
					if(nextchar == 'L'){
						number += 40;
						index = index+2;
					}
					else if(nextchar == 'C'){
						number += 90;
						index = index+2;
					}
					else{
						number += 10;
						index = index+1;
					}
				}
			}
			else if(romanNum.charAt(index) == 'C'){
				if(index == romanNum.length()-1){
					number += 100;
					index = index+1;
				}
				else{
					nextchar = romanNum.charAt(index+1);
					if(nextchar == 'D'){
						number += 400;
						index = index+2;
					}
					else if(nextchar == 'M'){
						number += 900;
						index = index+2;
					}
					else{
						number += 100;
						index = index+1;
					}	
				}
			}
			else if(romanNum.charAt(index) == 'M'){
				number += 1000;
				index = index+1;
			}
			else if(romanNum.charAt(index) == 'V'){
				number += 5;
				index = index+1;
			}
			else if(romanNum.charAt(index) == 'L'){
				number += 50;
				index = index+1;
			}
			else if(romanNum.charAt(index) == 'D'){
				number += 500;
				index = index+1;
			}
			
		}
		System.out.println("Arabic number is: "+number);
		System.out.println("Press any number to continue or 2 to exit");
		loopExit = Integer.parseInt(sc1.next());
		}while(loopExit != 2 );
	}

	
}

