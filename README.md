#include <stdio.h>
#include <stdlib.h>
#include <string.h>



// Structure to represent an incident
struct Incident {

    char name[30];
    int incidentId;
    char type[50];
    char date[20];
    char time[20];
    char affectedSystems[100];
    char description[500];
    char classification[50];
    char status[50];
    char assignedPersonnel[50];
    char resolutionSteps[500];

};



void heading();
void main_heading();
void displayMenu();
void logIncident();
void displayIncidents();
void performDataAnalysis();
void generateReport();
int authenticateUser();




int main() {

    heading();
    main_heading();

    struct Incident incidents[100]; // Assuming a maximum of 100 incidents

    int incidentCount = 0;
    int choice;

    do {
        displayMenu();
        scanf("%d", &choice);
        getchar(); // Consume the newline character

        switch (choice) {

            case 1:
                logIncident(incidents, &incidentCount);
                break;
            case 2:
                displayIncidents(incidents, incidentCount);
                break;
            case 3:
                performDataAnalysis(incidents, incidentCount);
                break;
            case 4:
                generateReport(incidents, incidentCount);
                break;
            case 5:
                printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t");
                printf("\n\t\t\t\t|          Exiting the program. Goodbye!         |\t\t");
                printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t\n");

                exit(0);

            default:
                printf("\n\n");
                printf("\t\t[ Invalid choice. Please try again. ]\n\n\n");
        }

    } while (choice != 5);

    return 0;

}



void heading()
{

    printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t");
    printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t");
    printf("\n\t\t\t\t|       WELCOME TO CYBER MANAGEMENT SYSTEM       |\t\t");
    printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t");
    printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t\n");

}



void main_heading()
{

    printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t");
    printf("\n\t\t\t\t|              CYBER MANAGEMENT SYSTEM            |\t\t");
    printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t\n");
    printf("\n");
    printf("\n");

}



// Main menu of the program
void displayMenu()
{

    printf("\n\t\t\t\t---------------------------------------------------\t\t\t\t");
    printf("\n\t\t\t\t Cyber Security Incident Logging and Analysis Tool \t\t");
    printf("\n\t\t\t\t---------------------------------------------------\t\t\t\t\n");

    printf("\n\n\n");
    printf("\t\t 1. Log an incident\n");
    printf("\t\t 2. Display all incidents\n");
    printf("\t\t 3. Perform data analysis\n");
    printf("\t\t 4. Generate incident report\n");
    printf("\t\t 5. Exit\n");
    printf("\t\t =========================================================\n");
    printf("\t\t Enter your choice: ");

}




// Function to log a new incident
void logIncident(struct Incident* incidents, int* incidentCount)
 {

    printf("\n\n");
    printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t");
    printf("\n\t\t\t\t|          Enter the details of the incident     |\t\t");
    printf("\n\t\t\t\t--------------------------------------------------\t\t\t\t\n");

    struct Incident newIncident;

    printf("\t\t Incident Name:");
    fgets(newIncident.name, sizeof(newIncident.name), stdin);
    newIncident.name[strcspn(newIncident.name, "\n")] = '\0';

    printf("\t\t Incident ID: ");
    scanf("%d", &newIncident.incidentId);
    getchar(); // Consume the newline character

    printf("\t\t Type: ");
    fgets(newIncident.type, sizeof(newIncident.type), stdin);
    newIncident.type[strcspn(newIncident.type, "\n")] = '\0'; // Remove trailing newline character

    // Prompt the user for date, time, affected systems, description

    printf("\t\t Classification: ");
    fgets(newIncident.classification, sizeof(newIncident.classification), stdin);
    newIncident.classification[strcspn(newIncident.classification, "\n")] = '\0';


    printf("\t\t Status: ");
    fgets(newIncident.status, sizeof(newIncident.status), stdin);
    newIncident.status[strcspn(newIncident.status, "\n")] = '\0';


    printf("\t\t Assigned Personnel: ");
    fgets(newIncident.assignedPersonnel, sizeof(newIncident.assignedPersonnel), stdin);
    newIncident.assignedPersonnel[strcspn(newIncident.assignedPersonnel, "\n")] = '\0';


    printf("\t\t Resolution Steps: ");
    fgets(newIncident.resolutionSteps, sizeof(newIncident.resolutionSteps), stdin);
    newIncident.resolutionSteps[strcspn(newIncident.resolutionSteps, "\n")] = '\0';


    incidents[*incidentCount] = newIncident;
    (*incidentCount)++;

    printf("\n");
    printf("\t\t Incident logged successfully!\n");

}



// Function to display all logged incidents
void displayIncidents(const struct Incident* incidents, int incidentCount)
{

    if (incidentCount == 0) {
        printf("No incidents logged yet.\n");
        return;

    }


    printf("\n");
    printf("\n\t\tLogged Incidents:                                 \t\t");
    printf("\n\t\t--------------------------------------------------\t\t\t\t\n");

    for (int i = 0; i < incidentCount; i++) {

        printf("\t\t Name: %s\n", incidents[i].name);
        printf("\t\t Incident ID: %d\n", incidents[i].incidentId);
        printf("\t\t Type: %s\n", incidents[i].type);
        printf("\t\t Classification: %s\n", incidents[i].classification);
        printf("\t\t Status: %s\n", incidents[i].status);
        printf("\t\t Assigned Personnel: %s\n", incidents[i].assignedPersonnel);
        printf("\t\t Resolution Steps: %s\n", incidents[i].resolutionSteps);
        printf("\n");
        // Display other details of the incident

    }
}



// Function to perform data analysis on incidents
void performDataAnalysis(const struct Incident* incidents, int incidentCount)
{

    // Perform analysis on incident data, such as counting frequency, identifying trends, etc.
    printf("\n");
    printf("\n\t\tPerforming data analysis:                         \t\t");
    printf("\n\t\t--------------------------------------------------\t\t\t\t\n");
    // Display analysis results
    printf("\t\t Analysis results:\n");
    printf("\t\t Total incidents logged: %d\n", incidentCount);
    // Display other analysis results as per your requirements

}



// Function to generate a summary report of incident data
void generateReport(const struct Incident* incidents, int incidentCount)
{

    // Generate a summary report based on incident data
    printf("\n");
    printf("\n\t\tGenerating report:                                \t\t");
    printf("\n\t\t--------------------------------------------------\t\t\t\t\n");

    // Open a file to write the report
    FILE* file = fopen("incident_report.txt", "w");
    if (file == NULL) {
        printf("Failed to create the report file.\n");
        return;

    }

    fprintf(file, "Incident Report\n");
    fprintf(file, "================\n\n");

    fprintf(file, "Total incidents logged: %d\n\n", incidentCount);

    fprintf(file, "Incidents:\n\n");
    for (int i = 0; i < incidentCount; i++) {
        fprintf(file, "Incident ID: %d\n", incidents[i].incidentId);
        fprintf(file, "Type: %s\n", incidents[i].type);
        fprintf(file, "Classification: %s\n", incidents[i].classification);
        fprintf(file, "Status: %s\n", incidents[i].status);
        fprintf(file, "Assigned Personnel: %s\n", incidents[i].assignedPersonnel);
        fprintf(file, "Resolution Steps: %s\n", incidents[i].resolutionSteps);
        fprintf(file, "\n");

    }

    fclose(file);

    printf("\t\tReport generated successfully!\n");

}




// Function to prompt user for credentials and validate them
int authenticateUser()
{

    char username[50];
    char password[50];

    printf("Username: ");
    fgets(username, sizeof(username), stdin);
    username[strcspn(username, "\n")] = '\0';

    printf("Password: ");
    fgets(password, sizeof(password), stdin);
    password[strcspn(password, "\n")] = '\0';

    // Perform authentication logic here
    // Return 1 if authentication is successful, 0 otherwise

    // Placeholder logic (always return 1 for demonstration purposes)
    return 1;

}









