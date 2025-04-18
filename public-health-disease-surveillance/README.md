# 🏥 Public Health Architecture Development: Communicable Disease Surveillance

## 📌 Project Overview
This project simulates a communicable disease surveillance system using virtual machines (VMs) to model a multi-node health network. The baseline architecture consists of five VMs: four hospital systems and one centralized Health Information Exchange (UPHIE). Each hospital VM is configured with OpenEMR, and the UPHIE node hosts a Dockerized HAPI-FHIR server for real-time data sharing and health data aggregation. This architecture reflects real-world scenarios in which data interoperability and public health reporting are essential.

---

## 🎯 Objectives
- Virtual Machine Configuration & Interconnectivity Testing  
- Installation, Configuration, and Security of OpenEMR  
- Generation of Synthea Patient and Syndromic Surveillance Data to Simulate Disease Outbreaks  
- Installation and Configuration of HAPI-FHIR Server  
- Enable Interoperability via FHIR Data Exchange  
- Aggregate and Visualize Disease Data for Public Health Surveillance

---

## 🧰 Tools & Technology

| Layer             | Technology / Tool                   |
|------------------|--------------------------------------|
| Virtualization    | VMware vCenter Cluster (MTU CCC)     |
| EHR Systems       | OpenEMR (v6.0.0)                     |
| Interoperability  | HAPI FHIR Server (Dockerized)       |
| API Testing       | Postman, Swagger UI                 |
| Operating System  | Ubuntu Server                       |
| Networking        | Custom VLAN (pv-stu-v3XXX)          |
| IP Addressing     | Static IPs per VM                   |

---

## 📂 VM Configuration

| Hospital / HIE           | Software   | IP Address      | HAPI-FHIR | OpenEMR | Pinged All VMs |
|--------------------------|------------|------------------|-----------|---------|----------------|
| Aspirus Hospital         | OpenEMR    | 192.168.17.90    | ❌        | ✅       | ✅              |
| Portage Health Hospital  | OpenEMR    | 192.168.17.91    | ❌        | ✅       | ✅              |
| BCMH                     | OpenEMR    | 192.168.17.92    | ❌        | ✅       | ✅              |
| MGH                      | OpenEMR    | 192.168.17.93    | ❌        | ✅       | ✅              |
| UPHIE (Central HIE)      | HAPI-FHIR  | 192.168.17.94    | ✅        | ❌       | ✅              |

---

## 🧪 Synthea Patient & Syndromic Data Simulation

Synthea was used to generate synthetic patient records to simulate disease outbreaks in each hospital EHR system. This enabled the testing of data flows from local EMRs to the centralized HIE using FHIR formats.

| Hospital       | % Used of Total Population Served | COVID-19 Patients Simulated |
|----------------|------------------------------------|-----------------------------|
| Aspirus        | Less than 1% of 5k                 | 30                          |
| Portage Health | Less than 1% of 9k                 | 50                          |
| BCMH           | Between 1% and 4% of 7k            | 150                         |
| MGH            | Greater than 5% of 20k             | 2000                        |

---

## ⚙️ System Architecture

This system models the flow of data from multiple hospitals to a central Health Information Exchange for monitoring and surveillance:

- 🏥 Each hospital VM runs **OpenEMR**, enabling EHR management at the local level.
- 🔄 Health records are initially in **HL7 format**, then converted into **FHIR resources** for standardization.
- 🌐 These resources are transmitted securely to the **UPHIE** node, which hosts a **HAPI-FHIR server**.
- 📊 Aggregated data is visualized using **Google Looker dashboards**, providing real-time insights into outbreaks and trends.

---

## 🚧 Challenges Faced
- Docker networking issues during initial HAPI-FHIR deployment.
- Manual configuration of Apache for OpenEMR across multiple VMs.
- Ensuring network connectivity and successful pinging between all VMs.
- Synchronizing FHIR resource formatting between OpenEMR and HAPI-FHIR endpoints.

---

## ✅ Outcomes
- Built and integrated a complete virtual EMR network with a centralized HIE.
- Enabled secure and standardized data exchange using the FHIR protocol.
- Gained hands-on experience configuring OpenEMR and HAPI-FHIR on VMs.
- Demonstrated real-time data visualization for public health surveillance.

---

## 👨‍⚕️ Contributors
- Keerthi Kesavan  

---

## 📄 License
This project is part of SAT5424 (Spring 2025) at Michigan Technological University. For academic use only.

