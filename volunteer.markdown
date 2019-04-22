**Nickolas Kusman. V 1.0. WC: 1819**

# Volunteer Computing 
# Abstract
At its core, volunteer computing is using the processing power of various heterogeneous devices within a distributed system in order to finish tasks for a singular project; usually one that would otherwise be too large for a single corporation/entity to solve itself. While volunteer computing could potentially be used in a corporate atmosphere, it is generally applied to fields in need of further scholarly research, such as folding proteins in the medical field. This is because volunteer computing allows researchers high-throughput computing at a low cost to researchers. The most common home to this large-scale volunteer computing is known as the Berkeley Open Infrastructure for Network Computing, or BOINC for short. While Volunteer Computing does have many benefits to research, it is not without its issues, such as volunteer drop-off and device heterogeneity, 

**Key Words**
**BOINC, Volunteer, Computing, Berkeley, Distributed, Systems, Gridcoin**

  # I. How Volunteer Computing works on a basic level#
Volunteer computing works on a client-server architecture. Each project has to host a project server, which is responsible for keeping project data, as well as distributing said data to the clients. The typical life cycle of a client-server interaction goes as follows:
Project Server sends the Client instructions to be completed
Project Server sends the Client Applications and input files 
Client Computes the assigned task from the Project Server
Client Uploads the output file to the Project Server
Client Reports results to the Project server 
After a task is completed, the client will request more tasks from the server, and the server will appoint jobs to the client. Until the process is interrupted, either by failure or user quitting a task, this cycle will continue indefinitely. Volunteer computing at its core is a distributed system, and a very simple yet efficient method to obtain a large amount of output data.

 #  II. Benefits of Volunteer Computing #

The benefits of volunteer computing are immense for the advancement of research; as previously mentioned, volunteer computing allows for high-throughput computing for a low cost to researchers. Currently, About 700,000 devices are actively participating in volunteer computing projects. These devices have about 4 million CPU cores and 560,000 GPUs, and collectively provide an average throughput of 93 PetaFLOPS. The devices are primarily modern, high-end computers: they average 16.5 CPU GigaFLOPS and 11.4 GB of RAM, and most have a GPU capable of general-purpose computing using OpenCL or CUDA. The potential capacity of volunteer computing is much larger: there are more than 2 billion consumer desktop and laptop computers [1]. For there to be such a massive interconnected web of processing power that only costs researchers servers and employees and the volunteers their internet connection and electricity, there is little justification to not to try to utilize volunteer on a greater scale. Due to this, there are incentives being created to help minimize the consumer loss in electricity, internet, and hardware cost to create more volunteers, known as Gridcoin. 

With the knowledge that there is an immense amount of untapped potential regarding consumer devices, one must ask how much cheaper would volunteer computing be in lieu of purchasing the computing power by itself? Well, operating a typical volunteer computing project involves a few Linux server computers and a part-time system administrator, costing the research project on the order of $100K per year. Several BOINC projects (Einstein@Home, SETI@home, Rosetta@home) are of this scale, and they average about 1 PetaFLOPS throughput each. How much would this computing power cost on Amazon EC2? According to Ostermann et al. [2], the best computing value is a node type that costs $0.24 per hour and provides 50 GigaFLOPS. It would take 20,000 such instances to provide 1 PetaFLOPS. This would cost $42 million per year – 420 times the cost of using VC. Kondo et al. compared the cost of volunteer and cloud computing in more detail, and reached a similar conclusion [3]. Because of this massive discrepancy in terms of cost of processing power, one can see how vast of a difference volunteer computing has had, and will have in the advancement of research.

   # III. Gridcoin, and Rewarding Volunteer Computing #
Gridcoin is an open-sourced blockchain that is responsible for both minting and distributing cryptocurrencies. Gridcoin can be exchanged for more common currencies, such as BTC or USD. Gridcoin is secured through the proof-of-stake cryptocurrency protocol, and is provided to the users who use volunteer computing to contribute to BOINC projects. According to the Gridcoin white paper, Gridcoin works as follows: “The Gridcoin blockchain genesis block was mined using a proof-of-work protocol on October 16th, 2013. Gridcoin continued as a proof-of-work blockchain until October 11th, 2014, when it forked onto a proof-of-stake protocol to secure the blockchain based on the number of active GRC on the Gridcoin network. Gridcoin has evolved through several iterations of proof-of-stake and incentive structures. Currently, proof-of-stake is used to secure the Gridcoin blockchain while the primary incentive structure is based on processing power contributed to approved BOINC projects. [4]. 

This proof-of-stake protocol is very useful for a field such as volunteer computing, as it is able to leverage both standard hardware, as well as more expensive hardware, which means all volunteers would be able to receive monetary compensation for their computing resources. This idea of incentivising the public to run these research programs on their computers, without any cost to the researchers, is a brilliant way to strengthen the total participation, and advance the sciences in general. 


  # IV. Detriments of Volunteer Computing #

Resource heterogeneity is an issue that is inherent in the field of using people’s spare resources; this is because the computers that are to be used are always going to have both different hardware configurations and different operating systems. So when creating a system to handle all of these units, creating a proper system with full interoperability is always going to be difficult. However, BOINC provides a framework that allows these research projects to utilize as many of these devices as possible, and it does it by providing separate platforms, or instructions for the combination of operating system/processor type. Because BOINC is able to distinguish the differences between the user systems, and correctly dole out the proper workload types for said computers, they are able to effectively bypass this issue with computer heterogeneity. 

A secondary issue that volunteer computing runs into is user impatience, or drop-off, where some jobs have to run for an extended period of time to complete, and the volunteers quit before a job can be properly completed. BOINC handles this issue by two different methods:
The application has the ability to tell the server that an output file is completed, and thus can push the intermediate data to the server.
The application can generate what are known as trickle-up messages, which are sent to the host server with the completed data and allow for the volunteer to receive partial credit for completing the task. 
By utilizing these two methods of output log recovery, BOINC can maintain the efficiency of its processes, and still manage to reward users even for leaving a particular job partially completed. Overall, while there are indubitably large issues when it comes to the formation of a fully functioning volunteer computing application, the way that BOINC has handled all of the potential issues proves that there are solutions to the downfalls of volunteer computing 

 #  V. BOINC and various @home projects #
The Berkeley Open Infrastructure for Network Computing, or BOINC, is the largest platform for research utilizing volunteer computing; This is because the server architecture and the client architecture are both ran incredibly efficiently. A BOINC research project must operate on a server which consists of a computer or computers running the server software. These servers center their work on a relational database, usually MariaDB or MySQL. These servers handle client RPCs via a scheduler, which tends to be implemented via a CGI or FCGI program ran from a web server. This scheduler’s main function is to dispatch jobs to clients. Additionally, a feeder process is in charge of retrieving unsent jobs and putting them into the server’s cache to be sent out later. In addition to the scheduler and the feeder processes, there are multiple separate daemon processes that are integral to the BOINC application, such as:

**Validator**: There is one for each app that uses replication. It examines the instances of a job, compares their output files, decides whether there is a quorum of equivalent results, and if so designates one instance as “canonical”. For apps that use homogeneous redundancy to achieve bitwise agreement between instances, BOINC supplies a validator that compares the output files byte for byte. Other apps use custom validators with a project-supplied function that does the (fuzzy) comparison for that app. 

**Assimilator**: This handles completed and validated jobs. There is one assimilator per app; it includes a project-supplied handler function. This function might move the output files to a particular destination, or parse them and write the results to a database.  

**Transitioner**: Viewing the progress of a job as a finite-state machine, this handles the transitions. The events that trigger transitions come from potentially concurrent processes like schedulers and validators. Instead of handling the transitions, these programs set a flag in the job’s database record. The transitioner enumerates these records and processes them. This eliminates the need for concurrency control of DB access.  

**File deleter**: This deletes input and output files of completed and assimilated jobs.
  
**Database purger**: This deletes the database records of completed jobs and job instances [5].

All of these separate processes allow the BOINC application to successfully distribute tasks and receive output files at an extremely efficient manner, leading to a very dependent platform for researchers to rely on for their work. Because of this, BOINC is responsible for providing a foundation for more than 30 separate research projects, such as:

SETI@home:  SETI (Search for Extraterrestrial Intelligence) is a scientific area whose goal is to detect intelligent life outside Earth. One approach, known as radio SETI, uses radio telescopes to listen for narrow-bandwidth radio signals from space. Such signals are not known to occur naturally, so a detection would provide evidence of extraterrestrial technology. [6]
Folding@home: The Folding@home project (FAH) is dedicated to understanding protein folding, the diseases that result from protein misfolding and aggregation, and novel computational ways to develop new drugs in general.
Enigma@Home: Enigma@home is a wrapper between BOINC and Stefan Krah's M4 Project. 'The M4 Project is an effort to break 3 original Enigma messages with the help of distributed computing. The signals were intercepted in the North Atlantic in 1942 and are believed to be unbroken.

These are just some of the potential applications that volunteer computing has, and with more development into volunteer computing and its incentivization, the potential for the depth and breadth of potential research is only its infancy.
