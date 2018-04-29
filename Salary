import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileWriter;
import java.io.IOException;

import java.util.Scanner;


public class Salary implements Raiseable {

	public static void main(String[] args) {

		Salary salary = new Salary();
		String fileName = "salary_data.txt";	
		String increasedSalaryFileName = "increased_salary_data.txt";


		salary.create(fileName); // creates new file

		salary.addTo(fileName, fileName, 11111, 26000.00, 12);
		//salary.addTo(fileName, fileName, 11111, 40000.00, 14);
		salary.addTo(fileName, fileName, 22222, 24000.00, 10);
		salary.addTo(fileName, fileName, 33333, 52000.00, 15);
		salary.addTo(fileName, fileName, 44444, 16400.00, 5);

		System.out.println("");
		System.out.println("Current Employee Salary Info: ");
		salary.display(fileName);
		System.out.println("");

		salary.addTo(fileName, fileName, 22222, 24000.00, 10);
		salary.addTo(fileName, fileName, 55555, 76000.00, 22);

		System.out.println("");
		System.out.println("Current Employee Salary Info: ");
		salary.display(fileName);
		System.out.println("");

		salary.removeFrom(fileName, fileName, 11111, 28000.00, 12);

		System.out.println("");
		System.out.println("Current Employee Salary Info: ");
		salary.display(fileName);
		System.out.println("");


		int salaryIncreased = salary.raise(fileName, increasedSalaryFileName, 15, 20);
		System.out.println("Number of Employees eligible for salary increase: " + salaryIncreased);
		System.out.println("Increased Employee Salary Info:");
		salary.display(increasedSalaryFileName);
		System.out.println("");

	}

	@Override
	public void create(String fileName) {
		BufferedWriter bw = null;

		try {
			FileWriter fw = new FileWriter(fileName); // creating filewriter to write txt to file
			bw = new BufferedWriter(fw);
			bw.flush();

		} catch (FileNotFoundException e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} catch (IOException e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} catch (Exception e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} finally {

			try {
				if (bw != null)
					bw.close();
			} catch (Exception e) {
				System.out.print("\n\n" + e.getClass() + " : ");
			    System.out.println(e.getMessage());
			}

		}

	}

	@Override
	public void display(String fileName) {

		Scanner reader = null;

		try {
			File file = new File(fileName);
			if (file.exists()) {
				reader = new Scanner(file);

				while (reader.hasNextLine()) {
					String line = reader.nextLine();

					if (line != null && !line.equalsIgnoreCase("")) {
						String lineArray[] = line.split(":");
						int id = Integer.parseInt(lineArray[0]);
						double salary = Double.parseDouble(lineArray[1]);
						int serviceYear = Integer.parseInt(lineArray[2]);
						System.out.println("ID: " + id + " Salary: " + salary + " Years of Service: " + serviceYear);
					}
				}	
			} else {

				System.out.println("Input file not found");	
			}

		} catch (FileNotFoundException e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} catch (Exception e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} finally {
			if (reader != null) {
				try {
					reader.close();
				} catch (Exception e) {
					System.out.print("\n\n" + e.getClass() + " : ");
				    System.out.println(e.getMessage());
				}
			}
		}

	}

	@Override
	public boolean addTo(String inFileName, String outFileName, int id, double salary, int yearsOfService) {

		Scanner reader = null;
		BufferedWriter bw = null;
		boolean flag = true;

		try {
			File file = new File(inFileName);
			if (file.exists()) {
				reader = new Scanner(file);
				while (reader.hasNextLine()) {
					String line = reader.nextLine();

					if (line != null && !line.equalsIgnoreCase("")) {
						String lineArray[] = line.split(":");
						int employeeID = Integer.parseInt(lineArray[0]);

						if (employeeID == id) {
							System.out.println(id + " already exists");
							flag = false;
							break;
						}

					}

				}
			} else {
				System.out.println("Input file not found");
			}

			if (flag) {

				FileWriter fw = new FileWriter(outFileName, true);
				bw = new BufferedWriter(fw);
				bw.write(id + ":" + salary + ":" + yearsOfService);
				bw.newLine();
				bw.flush();

			}

		} catch (FileNotFoundException e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} catch (Exception e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} finally {
			try {
				if (reader != null) {
					bw.close();
				}
			} catch (Exception e) {
				System.out.print("\n\n" + e.getClass() + " : ");
			    System.out.println(e.getMessage());
			}
		} 

		return flag;
	}

	@Override
	public boolean removeFrom(String inFileName, String outFileName, int id, double salary, int yearsOfService) {

		Scanner reader = null;
		BufferedWriter bw = null;
		boolean flag = false;
		try {
			String output = "";
			File file = new File(inFileName);
			if (file.exists()) {
				reader = new Scanner(file);
				while (reader.hasNextLine()) {
					String line = reader.nextLine();
					if (line!= null && !line.equalsIgnoreCase("")) {
						String lineArray[] = line.split(":");
						int employeeId = Integer.parseInt(lineArray[0]);
						if (employeeId == id) {
							System.out.println(id+" exists!");
							flag = true;
						} else {
							output = output + line + ";";
						}
					}
				}
			} else {
				System.out.println("Input File not found");
			}
			if (flag) {
				
				FileWriter fw = new FileWriter(outFileName);
				
				bw = new BufferedWriter(fw);
				String outputArray[] = output.split(";");
				for (int i=0;i<outputArray.length;i++) {
					bw.write(outputArray[i]);
					bw.newLine();
				}
				bw.flush();
			}
		} catch (FileNotFoundException e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} catch (Exception e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} finally {
			try {
				if (reader != null) {
					reader.close();
				}
				if (bw != null) {
					bw.close();
				}
			} catch (Exception e) {
				System.out.print("\n\n" + e.getClass() + " : ");
			    System.out.println(e.getMessage());
			}
		}
		return flag;
	}
	
	
	@Override
	public int raise(String inFileName, String outFileName, int yearsOfService,double salaryIncPercent) {
		
		Scanner reader = null;
		BufferedWriter bw = null;
		int count = 0;
		try {
			String output = "";
			File file = new File(inFileName);
			
			if (file.exists()) {
				
				reader = new Scanner(file);
				
				while (reader.hasNextLine()) {
					String line = reader.nextLine();
					if (line!= null && !line.equalsIgnoreCase("")) {
						
						String lineArray[] = line.split(":");
						int employeeId = Integer.parseInt(lineArray[0]);
						double salary = Double.parseDouble(lineArray[1]);
						int serviceYear = Integer.parseInt(lineArray[2]);
						
						if (serviceYear >= yearsOfService ) {
							salary = salary + ((salary*salaryIncPercent)/100);
							line = employeeId +":"+ salary + ":" + serviceYear;
							output = output + line + ";";
							count++;
						}
					}
				}
			} else {
				System.out.println("Input File not found");
			}
			if (count > 0) {
				
				FileWriter fw = new FileWriter(outFileName);
				
				bw = new BufferedWriter(fw);
				String outputArray[] = output.split(";");
				for (int i=0;i<outputArray.length;i++) {
					bw.write(outputArray[i]);
					bw.newLine();
				}
				bw.flush(); 
			}
		} catch (FileNotFoundException e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} catch (Exception e) {
			System.out.print("\n\n" + e.getClass() + " : ");
		    System.out.println(e.getMessage());
		} finally {
			try {
				if (reader != null) {
					reader.close();
				}
				if (bw != null) {
					bw.close();
				}
			} catch (Exception e) {
				System.out.print("\n\n" + e.getClass() + " : ");
			    System.out.println(e.getMessage());
			}
		}
		return count;
	}
	
	
	@Override
	public void mergeFiles(String inFileName1, String inFileName2, String outFileName) {
		
	}

}
