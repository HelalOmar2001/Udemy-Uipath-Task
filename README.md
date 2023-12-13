# UiPath Course Automation Project

This UiPath project automates the process of handling course requests, retrieving courses from Udemy, and sending the results to users via Outlook. The project is divided into two main parts: the Dispatcher and the Performer.

## Dispatcher

The Dispatcher is responsible for collecting incoming emails requesting courses in a specific field, adding these requests to the UiPath Orchestrator Queue for further processing.

### Steps:

1. **Collecting Emails:**
   - The Dispatcher monitors the specified inbox for incoming emails requesting courses.
   - It extracts relevant information such as the field of interest and user details.

2. **Adding to Orchestrator Queue:**
   - The extracted information is added to a queue in UiPath Orchestrator for subsequent processing by the Performer.

## Performer

The Performer processes the queued requests, logs into Udemy, searches for courses, and sends the results to users via Outlook. Additionally, it identifies courses exceeding the user's budget as a Business Exception and logs the results in a CSV file.

### Steps:

1. **Getting Data from Queue:**
   - Retrieve requests from the Orchestrator Queue processed by the Dispatcher.

2. **Logging into Udemy:**
   - Use automation to log into Udemy to search for courses.

3. **Fetching Courses:**
   - Retrieve the first 500 courses based on the specified criteria.

4. **Sending Courses via Outlook:**
   - Email the courses to the respective users using Outlook.
   - Label courses that exceed the user's budget as a Business Exception.

## Project Structure:

- **Dispatcher:**
  - `Main.xaml`: Main workflow for email processing and queue addition is located in the `Dispatcher` folder.

- **Performer:**
  - `Main.xaml`: Main workflow for processing queue items, searching Udemy, and sending emails is located in the `Performer` folder.

## Dependencies:

- UiPath Studio (compatible version)
- UiPath Orchestrator
- Outlook Application (for sending emails)
- Udemy Account

## Configuration:

1. Configure Orchestrator connection details in `config.xlsx`.
2. Update Udemy login details in `config.xlsx`.
3. Set up Outlook credentials.

## Execution:

1. Run the `Main.xaml` in `Dispatcher` to process incoming emails and add requests to the Orchestrator Queue.
2. Run the `Main.xaml` in `Dispatcher` to process queued requests, search Udemy, and send emails.

## Notes:

- Ensure all dependencies are installed and configured before executing the workflows.
- Monitor Orchestrator logs for any errors or exceptions.
- Review the Business Exceptions CSV file for courses exceeding the budget.
