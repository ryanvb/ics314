# ics314
iCal Project

/**
 * @description   iCal first Deliverable: Create an .ics file that is readable on any public .ics
 *                related application.
 * @author        Tsun Chu, Ryan Buillard, 
 * @date          2015.10.07
 */

import java.io.FileWriter;
import java.io.IOException;
import java.time.LocalDateTime;
import java.util.Scanner;

public class I_Cal 
{
	//main method
	public static void main(String args[]) throws IOException
	{
		Scanner scan = new Scanner(System.in);
		String filename = scan.nextLine();
		FileWriter fw = new FileWriter(filename + ".ics");
		fw.write("BEGIN:VCALENDAR\nPRODID:-//Google Inc//Google Calendar 70.9054//EN\n" +
				"VERSION:2.0\nCALSCALE:GREGORIAN\nMETHOD:PUBLISH\nX-WR-CALNAME:jurberry@gmail.com" + 
				"\nX-WR-TIMEZONE:Pacific/Honolulu\nBEGIN:VEVENT\nDTSTART:20150711T060000Z" + 
				"\nDTEND:20150711T070000Z\nDTSTAMP:20150711T044403Z\nUID:m64ebtqv877mke9dbobsnrotq4@google.com" +
				"\nCLASS:PUBLIC\nCREATED:20150711T044324Z\nDESCRIPTION:First iCal Deliverable" +
				"\nLAST-MODIFIED:20150711T044324Z\nLOCATION:University of Hawaii at Manoa, 2500 Campus Road, Honolulu, HI 96822, United States" 
				+ "\nSEQUENCE:0\nSTATUS:CONFIRMED\nSUMMARY:ics314 1st iCal Deliverable test\nTRANSP:OPAQUE" +
				"\nEND:VEVENT\nEND:VCALENDAR");
		scan.close();
		fw.close();
		//System.out.printf("This is the date: %s%n", LocalDateTime.now());
	}
}
