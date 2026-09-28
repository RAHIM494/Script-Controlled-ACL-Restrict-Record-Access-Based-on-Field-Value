(function () {
    // Allow admin users full access
    if (gs.hasRole('admin')) {
        return true; //
    }

    // Allow only users with the 'bb1' role to see EEE records
    if (gs.hasRole('bb1')) {
        return true; //
    }

    // Deny access for all other users
    return false; //
})();
# ServiceNow Script-Controlled ACL Lab

This repository contains the setup, configurations, and scripts for implementing script-controlled Access Control Lists (ACLs) in ServiceNow to restrict record access based on field values and user roles.

## Lab Description
This lab demonstrates how to restrict record access on a custom table (`u_institution_details`) using role-based permissions combined with script evaluation and data conditions.

## Custom Table Details
- **Table Label:** Institution Details
- **Table Name:** `u_institution_details`
- **Fields:**
  - `Student Roll Number` (Auto Number)
  - `Student Name` (Reference -> User)
  - `Faculty Name` (Reference -> User)
  - `Branch` (Choice: ECE, EEE, CSE)
  - `Email` (String)
  - `Phone Number` (String)
  - `Description` (Multi String)

## Roles & Access Matrix
- **`bb1`**: Grants **Read** access to records where `Branch = EEE`.
- **`bb2`**: Grants **Create** access for new records.
- **`bb3`**: Grants **Write** (edit) access to existing records.
- **`bb4`**: Grants **Delete** access to records.
(function () {
    // Allow admin users full access
    if (gs.hasRole('admin')) {
        return true;
    }

    // Allow only users with the 'bb1' role to see EEE records
    if (gs.hasRole('bb1')) {
        return true;
    }

    // Deny access for all other users
    return false;
})();