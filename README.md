# live-code
Live Coding Challenge: GDPR-Compliant User Consent System with Flexible Strategies

Scenario:

You are tasked with building a part of a GDPR-compliant system for managing user data. Specifically, your team wants a flexible solution for processing user consent, as different user types may require different consent validation rules.

Your goal is to implement the core functionality for user creation and consent handling using the Strategy Pattern.

Requirements:

User Model:
Implement a basic User model with the following fields:

id (UUID, auto-generated)

email (String, required, must be valid)

role (Enum: USER, ADMIN, required)

consentGiven (Boolean, required for role USER)

consentTimestamp (LocalDateTime, set when consent is processed)

Consent Strategies:
Create three strategies to handle consent processing:

StandardConsentStrategy: Requires consentGiven to be explicitly true.

AdminImpliedConsentStrategy: Automatically sets consentGiven = true for users with the role ADMIN.

Service Layer:
Implement a UserService that:

Accepts user input and determines the correct consent strategy to use based on the user's role or other attributes.

Processes consent using the selected strategy.

Returns the created user with all fields populated, including id and consentTimestamp.

Controller Endpoint:

POST /users

Accepts a JSON payload with user details (email, role, consentGiven if applicable).

Creates a user using the service layer.

Returns the created user as JSON.
