# SentinelOpenAIProcessor

## Overview
The `SentinelOpenAIProcessor` automation integrates Microsoft Sentinel with Azure OpenAI services to analyze security incidents and generate structured SOAP (Subjective, Objective, Assessment, Plan) notes. These notes provide actionable insights for incident responders by summarizing key information about security incidents detected by Microsoft Sentinel.

This automation uses Azure Logic Apps to:
1. Fetch incident details from Microsoft Sentinel.
2. Send the details to an Azure OpenAI endpoint.
3. Generate SOAP notes based on the incident data.
4. Optionally add comments with the SOAP notes back to the incident in Sentinel.

---

## Features
- **Incident Analysis:** Fetches detailed incident information from Sentinel.
- **SOAP Note Generation:** Uses Azure OpenAI to create structured SOAP notes based on incident data.
- **Automated Documentation:** Comments the SOAP notes back to the Sentinel incident for easy reference.
- **Error Handling:**

---

## Prerequisites
### Azure Resources
1. **Microsoft Sentinel:** Ensure Sentinel is configured and has active incidents.
2. **Azure OpenAI:** Deploy an OpenAI model endpoint (e.g., `gpt-4`) with a valid API key.

### Permissions
- The Azure Logic App must have permission to:
  - Access Microsoft Sentinel incidents.
  - Use the Azure OpenAI endpoint.
  - Write comments back to Sentinel incidents

---

## Workflow
### Step-by-Step Process
1. **Get Incident:**
   - Fetches incident details from Microsoft Sentinel using the `Get incident` step.

2. **For Each Incident:**
   - Iterates through each incident fetched.

3. **HTTP Request to Azure OpenAI:**
   - Sends the incident details to the Azure OpenAI endpoint with a structured prompt.
   - Example Prompt:
     ```
     You are a cybersecurity analyst. Analyze the following Sentinel incident details and generate a structured SOAP note...
     ```

4. **Parse JSON Response:**
   - Parses the response from Azure OpenAI to extract the SOAP note content.

5. **Optional: Add Comment to Incident:**
   - Adds the generated SOAP note as a comment back to the Sentinel incident for documentation.

---

## Setup Instructions
### Deployment
1. Clone the GitHub repository containing this Logic App.
2. Deploy the Logic App using the Azure Portal or ARM templates.
3. Update the Logic App configuration with:
   - Sentinel workspace details.
   - Azure OpenAI endpoint and API key.

### Configuration
- **HTTP Action:**
  - Update the URL, headers, and body to match your Azure OpenAI endpoint.
- **Parse JSON Action:**
  - Ensure the schema matches the actual OpenAI response.
- **Add Comment Action:**
  - Configure the connection to your Sentinel workspace.

---

## License
This project is licensed under the MIT License. See the LICENSE file for details.

---

## Acknowledgments
- **Microsoft Sentinel** for providing comprehensive threat detection capabilities.
- **Azure OpenAI** for enabling advanced natural language processing and analysis.
