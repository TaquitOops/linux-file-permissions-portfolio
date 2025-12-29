# Using Linux Commands to Manage File Permissions

## Project Description

In this project, file and directory permissions within the `projects` directory were reviewed
and updated to ensure they reflect the correct level of authorization. Incorrect permissions
can pose a security risk, so the goal of this activity was to verify existing permissions and
modify them as needed using Linux commands.

---

## Checking File and Directory Permissions

To review the existing permissions for files and directories, including hidden files,
the following command was used:

    ls -la projects

This command provides a detailed list of all files and directories within the `projects`
directory. The output includes permission strings, ownership information, and file types.

---

## Understanding the Permission String

Each file or directory has a permission string consisting of 10 characters:

- **1st character:** Indicates the file type  
  - `d` = directory  
  - `-` = regular file  

- **Characters 2–4:** User permissions (read, write, execute)  
- **Characters 5–7:** Group permissions  
- **Characters 8–10:** Permissions for others  

### Example

    -rw-rw-r--

This permission string indicates:

- The item is a regular file  
- The user and group have read and write permissions  
- Other users have read-only permissions  
- No execute permissions are granted  

---

## Modifying File Permissions

The organization decided that other users should not have write access to any files.
To remove write permission for others from the file `project_k.txt`, the following command
was executed:

    chmod o-w project_k.txt

After applying the change, permissions were verified again using `ls -la`.

---

## Modifying Permissions on a Hidden File

The file `.project_x.txt` is a hidden file that has been archived. No users should have
write access to this file, but the user and group should retain read access.

To achieve this, the following commands were used:

    chmod u-w .project_x.txt
    chmod g-w,g+r .project_x.txt

These commands removed write permissions from both the user and group while ensuring
the group retained read access.

---

## Modifying Directory Permissions

The organization requires that only the user `researcher2` has access to the `drafts`
directory and its contents. This means that execute permissions should be removed
from the group and other users.

    chmod g-x,o-x drafts

After executing this command, the directory permissions were reviewed to confirm
the changes.

---

## Summary

In this activity, Linux commands were used to inspect and manage file and directory
permissions. The `ls -la` command was used to review existing permissions, and the
`chmod` command was used to modify them according to organizational security
requirements. Proper permission management helps ensure that only authorized users
have access to sensitive files and directories.
