# Reading: Access Control (ACL)

## access control list (ACL)

Is a list of rules that specifies which user or systems granted or denied access to particular object or system resource. Access control lists are used to control permission to a computer system or computer network. They are used to filter traffic in and out of a specific device.

## What is Role Based Access Control (RBAC) :

Role Based Access Control (RBAC) : is the idea of assigning system access to users based on their role within an organization.

## RBAC definition :

The system needs of a given workforce are analyzed, with users grouped into roles based on common job responsibilities and system access needs. Access is then assigned to each person based strictly on their role assignment. With tight adherence to access requirements established for each role, access management becomes much easier.

One reason RBAC is not used more frequently is that for small to medium sized companies, it seems easier to just do this on an ad-hoc basis as each employee joins the company. The challenge is that with as many permutations as can exist with just a few systems involved, the approach becomes unsustainable.

## RBAC Benefits :

- Security : 

    RBAC improves overall security as it relates to compliance, confidentiality, privacy, and access management to resources and other sensitive data and systems.

- Selective access : 

    RBAC systems can support users having multiple roles at the same with specific permissions for each role.

- Security as a function of organizational structure : 

    Allows organizations to impose - hierarchies for assigning permissions based on the seniority or topology of organizations.

- Separation of duties (SoD) : 

    Is the concept that no one person has sole control over a task. SoD benefits organizations as cyber-attacks on a single account won’t cause significant harm to systems.

- Flexibility : 

    IT organizations can review and adjust permissions associated with each role periodically.

With the proper implementation of RBAC, the assignment of access rights becomes systematic and repeatable. Further, it is much easier to audit user rights, and to correct any issues identified.

## RBAC implementation :

1. Inventory your systems :

   Figure out what resources you have for which you need to control access, if you don't already have them listed.

2. Analyze your workforce and create roles :

   You need to group your workforce members into roles with common access needs. Avoid the temptation to have too many roles defined. Keep them as simple and stratified as possible.

3. Assign people to roles :

   Now that you have a list of roles and their access rights, figure out which role(s) each employee belongs in, and set their access accordingly.

4. Never make one-off changes :

   Resist any temptation to make a one-off change for an employee with unusual needs. If you begin doing this, your RBAC system will quickly begin to unravel. Change the roles as required or add new ones when really necessary.

5. Audit :

   Periodically review your roles, the employees assigned to them, and the access permitted for each. If you discover, for example, that a role has unnecessary access to a particular system, change the role and adjust the access level for all employees in that role.

## Three primary rules defined for RBAC :

1. Role assignment :

   A subject can exercise a permission only if the subject has selected or been assigned a role.

2. Role authorization :

   A subject's active role must be authorized for the subject.

3. Permission authorization :
   A subject can exercise a permission only if the permission is authorized for the subject's active role.

# References :

- [5 steps to RBAC](https://www.csoonline.com/article/3060780/5-steps-to-simple-role-based-access-control.html)

- [wiki - RBAC](https://en.wikipedia.org/wiki/Role-based_access_control)

- [RBAC tutorial](https://www.youtube.com/watch?v=C4NP8Eon3cA&ab_channel=Udacity)
