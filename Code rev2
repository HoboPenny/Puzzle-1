import java.util.*;

public class PuzzleSolver {
    static class Student {
        String name;
        String language;
        List<String> problems;

        Student(String name, String language, List<String> problems) {
            this.name = name;
            this.language = language;
            this.problems = problems;
        }

        @Override
        public String toString() {
            return name + " uses " + language + " and solves " + problems;
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        Set<String> languages = new HashSet<>(Arrays.asList("Python", "Java", "C++", "Ruby", "Swift"));
        Set<String> problems = new HashSet<>(Arrays.asList("Math", "Logic", "Sorting", "Graph"));

        List<Student> studentAssignments = new ArrayList<>();

        System.out.println("Enter the number of students:");
        int numberOfStudents = Integer.parseInt(scanner.nextLine());

        for (int i = 0; i < numberOfStudents; i++) {
            System.out.println("Enter student name:");
            String name = scanner.nextLine();

            System.out.println("Enter programming language (Python, Java, C++, Ruby, Swift):");
            String language = scanner.nextLine();
            while (!languages.contains(language)) {
                System.out.println("Invalid language. Please enter one of the following: Python, Java, C++, Ruby, Swift:");
                language = scanner.nextLine();
            }

            System.out.println("Enter problems solved (comma-separated, e.g., Math, Logic):");
            String[] problemArray = scanner.nextLine().split(",");
            List<String> problemList = new ArrayList<>();
            for (String problem : problemArray) {
                String trimmedProblem = problem.trim();
                if (problems.contains(trimmedProblem)) {
                    problemList.add(trimmedProblem);
                } else {
                    System.out.println("Invalid problem: " + trimmedProblem + ". It will be ignored.");
                }
            }

            studentAssignments.add(new Student(name, language, problemList));
        }

        studentAssignments.sort(Comparator.comparing(student -> student.name));

        System.out.println("\nStudent-to-Language Relation:");
        for (Student student : studentAssignments) {
            System.out.println(student.name + " -> " + student.language);
        }

        System.out.println("\nStudent-to-Problem Relation:");
        for (Student student : studentAssignments) {
            System.out.println(student.name + " -> " + student.problems);
        }

        Map<String, Integer> languageProblemCount = new HashMap<>();
        for (Student student : studentAssignments) {
            languageProblemCount.put(student.language, languageProblemCount.getOrDefault(student.language, 0) + student.problems.size());
        }

        System.out.println("\nProblems solved by each language:");
        for (Map.Entry<String, Integer> entry : languageProblemCount.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue() + " problems solved");
        }

        scanner.close();
    }
}
