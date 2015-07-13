import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;
import java.time.LocalDateTime;

/**@description iCal first Deliverable: Create an .ics file that is readable on any public .ics
 * related application
 * 
 * @author Tsun Chu, Ryan Buillard 
 * @date 2015.10.07
 */
public class I_Cal {

	// Main Method
	public static void main(String args[]) throws IOException {

		/** Starting Variables */

		Scanner scan = new Scanner(System.in);
		// Time Variables
		String startH, startM, endH, endM;
		// Date Variables
		String event, description, classification, startD, endD;
		// Geographic Position Variables
		String location, geo1, geo2, geoA;

		// Here is where the console starts
		System.out.println("What do you want the file to be called?");

		String filename = scan.nextLine();
		FileWriter fw = new FileWriter(filename + ".ics");

		System.out.println("Please enter name of event: ");
		event = scan.nextLine();

		System.out.println("Please enter the location/address: "
		+ "Ex. University of Hawaii at Manoa, 2500 Campus Road, Honolulu, HI 96822, United States"); 
		location = scan.nextLine();
		
		System.out.println("Type in any extra notes: ");
		description = scan.nextLine();

		System.out.println("Is the classification- Public, Private or Confidential? Please type in all caps: ");
		classification = scan.nextLine();

		System.out.println("Do you want to put the geographic position? Yes or no");
		geoA = scan.nextLine();
		
		if (geoA.equalsIgnoreCase("yes")) {
			System.out.println("Enter the latitude and longitude separated by a semicolon. Ex. 37.386013;-122.082932");
			geo2 = scan.nextLine();
			geo1 = "\nGEO:";
		} 
		else {
			geo1 = "";
			geo2 = "";
		}
		
		System.out.println("What is the date of the event? Ex. 20150711");
		startD = scan.nextLine();
		
		System.out.println("Time starting? Just hour Ex. 00 for 12am, 23 for 11pm");
		startH = scan.nextLine();
		
		System.out.println("Now minute? Ex. 01 for 1 minute, 59 for 59 minutes");
		startM = scan.nextLine();
		
		System.out.println("What date is it ending?");
		endD = scan.nextLine();

		System.out.println("Time ending? Just hour Ex. 00 for 12am, 23 for 11pm");
		endH = scan.nextLine();
		
		System.out.println("Now minute? Ex. 01 for 1 minute, 59 for 59 minutes");
		endM = scan.nextLine();

		fw.write("BEGIN:VCALENDAR"
				+ "\nPRODID:-//Google Inc//Google Calendar 70.9054//EN"
				+ "\nVERSION:2.0" + "\nCALSCALE:GREGORIAN" + "\nMETHOD:PUBLISH"
				+ "\nX-WR-CALNAME:jurberry@gmail.com"
				+ "\nX-WR-TIMEZONE:Pacific/Honolulu" + "\nBEGIN:VEVENT"
				+ "\nDTSTART:" + startD + "T" + startH + startM + "00Z"
				+ "\nDTEND:" + endD + "T" + endH + endM + "00Z"
				+ "\nDTSTAMP:" + LocalDateTime.now()
				+ "\nUID:m64ebtqv877mke9dbobsnrotq4@google.com"
				+ geo1
				+ geo2
				+ "\nDESCRIPTION:" + description
				+ "\nCLASS:" + classification
				+ "\nCREATED:" + LocalDateTime.now()
				+ "\nLAST-MODIFIED:" + LocalDateTime.now()
				+ "\nLOCATION:" + location				
				+ "\nSEQUENCE:0"
				+ "\nSTATUS:CONFIRMED"
				+ "\nSUMMARY:" + event
				+ "\nTRANSP:OPAQUE" + "\nEND:VEVENT" + "\nEND:VCALENDAR");

		//Close FileWriter and Scanner
		scan.close();
		fw.close();

	}
}
