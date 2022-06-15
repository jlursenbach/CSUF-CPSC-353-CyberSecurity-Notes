# Chapter 4 Access Control

## Definition:

### NISTIR 7298 defines access control as:

```
	“the process of granting or denying specific requests to: (1) obtain and use information and related information processing services; and (2) enter specific physical facilities ”

```

### RFC 4949 defines access control as:

```
	a process by which use of system resources is regulated according to a security policy and is permitted only by authorized entities (users, programs, processes, or other systems) according to that policy

```

`

## Table 4.1

### Access Control Security Requirements   ( SP 800-171

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled.png)

1) Limit information system access to authorized used, process acting on behelf of authorized users, or devices (including other information systems)

2

3

4

## Access Control Principles

In a broad sense, all of computer security is concerned with access control

RFC 4949 defines computer security as:

```
	“measures that implement and assure security services in a computer system, particularly those that assure access control service”

```

## Access Control Policies

### Discretionary access control (DAC)

Controls access based on the identity of the requestor and on access rules (authorizations) stating what requestors are (or are not) allowed to do

### Mandatory access control (MAC)

Controls access based on comparing security labels with security clearances

### Role-based access control (RBAC)

Controls access based on the roles that users have within the system and on rules stating what accesses are allowed to users in given roles

### Attribute-based access control (ABAC)

Controls access based on attributes of the user, the resource to be accessed, and current environmental conditions

## Subjects, Objects, and Access Rights

### Subjects

An entity capable of accessing objects

Three classes:
- Owner
- Group
- World

### Objects

A resource to which access is controlled

Entity used to contain and/or receive information

### Access Rights

Describes the way in which a subject may access an object

Could include:
- Read
- Write
- Execute
- Delete
- Create
- Search

## Discretionary Access Control (DAC)

- Scheme in which an entity may be granted access rights that permit the entity, by its own violation, to enable another entity to access some resource
- Often provided using an access matrix
    - One dimension consists of identified subjects that may attempt data access to the resources
    - The other dimension lists the objects that may be accessed
- Each entry in the matrix indicates the access rights of a particular subject for a particular object

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%201.png)

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%202.png)

Table 4.2

Authorization Table
for Files in Figure 4.2

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%203.png)

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%204.png)

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%205.png)

Access Control System commands:

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%206.png)

## Protection Domains

- Set of objects together with access rights to those objects
- More flexibility when associating capabilities with protection domains
- In terms of the access matrix, a row defines a protection domain
- User can spawn processes with a subset of the access rights of the user
- Association between a process and a domain can be static or dynamic
- In user mode certain areas of memory are protected from use and certain instructions may not be executed
- In kernel mode privileged instructions may be executed and protected areas of memory may be accessed

## UNIX File Access Control

### UNIX files are administered using inodes (index nodes)

- Control structures with key information needed for a particular file
- Several file names may be associated with a single inode
- An active inode is associated with exactly one file
- File attributes, permissions and control information are sorted in the inode
- On the disk there is an inode table, or inode list, that contains the inodes of all the files in the file system
- When a file is opened its inode is brought into main memory and stored in a memory resident inode table

### Directories are structured in a hierarchical tree

- May contain files and/or other directories
- Contains file names plus pointers to associated inodes

### File Access Control

- Unique user identification number (user ID)
- Member of a primary group identified by a group ID
- Belongs to a specific group
- 12 protection bits
- Specify read, write, and execute permission for the owner of the file, members of the group and all other users
- The owner ID, group ID, and protection bits are part of the file’s inode

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%207.png)

## Traditional UNIXFile Access Control

- “Set user ID”(SetUID)
- “Set group ID”(SetGID)
    - System temporarily uses rights of the file owner/group in addition to the real user’s rights when making access control decisions
    - Enables privileged programs to access files/resources not generally accessible
- Sticky bit
    - When applied to a directory it specifies that only the owner of any file in the directory can rename, move, or delete that file
- Superuser
    - Is exempt from usual access control restrictions
    - Has system-wide access

## Access Control Lists (ACLs)in UNIX

### Modern UNIX systems support ACLs

FreeBSD, OpenBSD, Linux, Solaris

### FreeBSD

- Setfacl command assigns a list of UNIX user IDs and groups
- Any number of users and groups can be associated with a file
- Read, write, execute protection bits
- A file does not need to have an ACL
- Includes an additional protection bit that indicates whether the file has an extended ACL

### When a process requests access to a file system object two steps are performed:

- Step 1 selects the most appropriate ACL
- Step 2 checks if the matching entry contains sufficient permissions
- 

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%208.png)

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%209.png)

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%2010.png)

Table 4.4Scope RBAC Models

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%2011.png)

![Untitled](Chapter%204%20Access%20Control%20e6362e152d8c410fba062035ac95ec4a/Untitled%2012.png)

## Constraints - RBAC

- Provide a means of adapting RBAC to the specifics of administrative and security policies of an organization
- A defined relationship among roles or a condition related to roles

### Mutually exclusive roles

- A user can only be assigned to one role in the set (either during a session or statically)
- Any permission (access right) can be granted to only one role in the set

### Cardinality

- Setting a maximum number with respect to roles

### Prerequisite roles

- Dictates that a user can only be assigned to a particular role if it is already assigned to some other specified role

## Attribute-Based Access Control (ABAC)

- Can define authorizations that express conditions on properties of both the resource and the subject
- Strength is its flexibility and expressive power
- Main obstacle to its adoption in real systems has been concern about the performance impact of evaluating predicates on both resource and user properties for each access
- Web services have been pioneering technologies through the introduction of the eXtensible Access Control Markup Language (XAMCL)
- There is considerable interest in applying the model to cloud services

## ABAC Model: Attributes

### Subject attributes

- A subject is an active entity that causes information to flow among objects or changes the system state
- Attributes define the identity and characteristics of the subject

### Object attributes

- An object (or resource) is a passive information system-related entity containing or receiving information
- Objects have attributes that can be leverages to make access control decisions

### Environment attributes

- Describe the operational, technical, and even situational environment or context in which the information access occurs
- These attributes have so far been largely ignored in most access control policies

# ABAC

- Distinguishable because it controls access to objects by evaluating rules against the attributes of entities, operations, and the environment relevant to a request
- Relies upon the evaluation of attributes of the subject, attributes of the object, and a formal relationship or access control rule defining the allowable operations for subject-object attribute combinations in a given environment
- Systems are capable of enforcing DAC, RBAC, and MAC concepts
- Allows an unlimited number of attributes to be combined to satisfy any access control rule

## ABAC Policies

A policy is a set of rules and relationships that govern allowable behavior within an organization, based on the privileges of subjects and how resources or objects are to be protected under which environment conditions

Typically written from the perspective of the object that needs protecting and the privileges available to subjects

Privileges represent the authorized behavior of a subject and are defined by an authority and embodied in a policy

Other terms commonly used instead of privileges are: rights, authorizations, and entitlements

## Identity, Credential, and Access Management (ICAM)

- A comprehensive approach to managing and implementing digital identities, credentials, and access control
- Developed by the U.S. government
- Designed to:
    - Create trusted digital identity representations of individuals and nonperson entities (NPEs)
    - Bind those identities to credentials that may serve as a proxy for the individual of NPE in access transactions
        - A credential is an object or data structure that authoritatively binds an identity to a token possessed and controlled by a subscriber
    - Use the credentials to provide authorized access to an agency’s resources
    
    ## Identity Management
    
- Concerned with assigning attributes to a digital identity and connecting that digital identity to an individual or NPE
- Goal is to establish a trustworthy digital identity that is independent of a specific application or context
- Most common approach to access control for applications and programs is to create a digital representation of an identity for the specific use of the application or program
- Maintenance and protection of the identity itself is treated as secondary to the mission associated with the application
- Final element is lifecycle management which includes:
    - Mechanisms, policies, and procedures for protecting personal identity information
    - Controlling access to identity data
    - Techniques for sharing authoritative identity data with applications that need it
    - Revocation of an enterprise identity

## Credential Management

Hello

## Access Management