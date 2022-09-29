# SortingApp
This is a sort app to sort the contents of this file in ascending order first by the length of the name, then alphabetically.

import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;
import java.util.Comparator;

public class SortApp { 
private static final String FILE_PATH = "/Users/asumi/Desktop/Sort Me.txt";

  public static void main(String[] args) {
      String[] name;
      List<String> nameList = new ArrayList<String>();
          // Read file
          read(nameList);
          //Sort in ascending order of string length
          nameList.sort(Comparator.comparing(String::length).thenComparing(Comparator.naturalOrder()));
          // convert list of names to array

          name = (String[])nameList.toArray(new String[0]);

          for (String theName : name) {
              System.out.println(theName);
          }
          System.out.println();          
  }

  private static void read(List<String> nameList) {
      BufferedReader br = null;
      try {
          br = new BufferedReader(new FileReader(FILE_PATH));
          String line = br.readLine();
          // Read file
          while (line != null) {
              String[] array = line.strip().split("\n");

              if (array.length != 0) {
                  nameList.add(array[0]);
                  line = br.readLine();
              }

          }

      //Error handling
      } catch (FileNotFoundException e) {
          e.printStackTrace();
      } catch (IOException e) {
          e.printStackTrace();
      } finally {
      try {
          if (br != null) {
              br.close();
          }
      } catch (IOException e) {
          e.printStackTrace();
      }
      }
  }
  }
