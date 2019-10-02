ESC 2019 Challenge Description
==============================


The theme of this year's ESC competition is **exploiting the firmware of a vulnerable radio frequency identification (RFID) card reader**. RFID readers are widely used for authentication and access control in buildings and computer systems. While it is possible to clone RFID cards, this challenge will go one step further, tasking the users to reverse engineer a custom RFID reader firmware and create exploits that allow them to bypass the security protections of the system. Contestants will be provided with a custom card reader, the firmware, and will utilize the recently released Ghidra reverse engineering tool (developed by the United States National Security Agency) to reverse engineer the system. Contestants can expect to learn:
  1. The NSA Ghidra Tool
  2. Firmware Exploitation
  3. RFID Protocols

The ESC 2019 competition will strengthen students' understanding of firmware exploitation and familiarize them with industry tools in an interactive environment.



## Technical Requirements

The high-level focus and competition requirements are as follows:
-   The focus of the competition is to reverse engineer and exploit the firmware of a binary firmware file.
-   Competitors will require access to a computer with the [Arduino IDE](https://www.arduino.cc/en/Main/Software), [TeensyDuino](https://www.pjrc.com/teensy/teensyduino.html), and the [Ghidra Reverse Engineering Tool](https://github.com/NationalSecurityAgency/ghidra)
-   Competitors will require access to a soldering iron for assembling the provided almost-ready-to-use PCB kit

See the [grading details](#grading) below for more information on grading.


## Challenge structure

The ESC19 competition is divided into three phases:

1. A preliminary **Qualification phase**, where teams must compile and submit a written report characterizing exploits and reverse engineering techniques that they utilized to break a provided program.

2. A **Final phase**, where qualified teams are invited to the CSAW event of their region to present and demonstrate their attack implementations on the custom systems provided by the organizers.

3. A **Live phase**, where qualified teams will be provided with a special challenge binary on the day of the ESC finals in their region. The contestants will then race to solve the challenge, demonstrating their reverse engineering prowess!

See below for more details on the requirements of each phase.


### Qualification Phase

For the qualification phase, participating teams are invited to **reverse engineer** a [provided vulnerable binary](qualification.out) using **Ghidra** and develop exploits using different approaches and techniques. In addition, teams should submit a **write-up** that outlines their approaches and techniques (not necessarily only one approach/technique) utilized to reverse engineer the provided binary. To that end, the proposal should also explore existing techniques on the topic, focusing on (but not necessarily limited to) firmware exploitation and RFID hacking. The best approaches will include a discussion of existing techniques, a clear outline of reverse engineering methodologies, and a demonstration of the success and effectiveness of the team's strategy. 

Qualification phase reports will be evaluated by a team of experts, and will take into account the **correctness** and **creativity** of the applied reverse-engineering techniques, as well as the completeness and quality of the compiled report.

### Final Phase

The top teams of each region (US-Canada, Europe, MENA, India) will qualify for the final phase, which will require **implementing** and **demonstrating** firmware-level attacks on a series of increasingly secure programs. Each exploited program will be worth a number of points depending on its difficulty.

A detailed description of the final phase [is provided here](final_phase.md).

The teams should compose a **final report** detailing their approaches. The definitive goal is to demonstrate their methods during the live demos.

### Live Phase

On the day of the finals, each region will receive a live challenge binary. This binary will have a new challenge that teams will race to solve as quickly as possible during the competition. Teams should come prepared with the provided PCB so that they can program their RFID card on site with an exploitation payload to defeat the live challenge. A special RFID lock will be programmed with the live challenge by the organizers and will be ready to be exploited; when a team is confident that they have developed a working exploit, they will scan their programmed RFID card at the RFID lock and attempt to unlock it. As this phase is a race, the first team to successfully complete it will receive 150 extra points to their final challenge score. The second team will receive 100 extra points, and the third team will receive 50 extra points. No other teams will receive extra points. 

## Evaluation and Grading Policies
Within the final phase, there will be a series of challenges for teams to solve. Challenges will be provided in terms of increasing difficulty, but participants can solve challenges in any order that they wish.

The evaluation of the finalists will be the responsibility of a panel of **industry expert judges** in each region. During the day of the finals, each team should be able to answer the questions posed by the judges and **demonstrate their exploits live**. Furthermore, the finalists are required prepare a **Powerpoint presentation** of their work and a **short video** to present on the day of the finals, complementing their submitted **final report**. On the day of the finals, demonstration of the proposed attacks will be the responsibility of each team.

The final phase will be graded as follows:
- 50% of the final score will be correctness. The points awarded in this section are based on successfully solving the provided challenges and depend on the difficulty of each challenge. The awarded points will be determined automatically by the provided firmware.
- 10% of the score will be performance and efficiency. Performance will be evaluated by a panel of expert judges and will encompass the techniques that the participants utilize to solve the challenges. For example, utilizing an exhaustive test for every possible answer would be rated as very inefficient, whereas a solution that examines a process and can determine an exact solution would be rated as very efficient.
- 10% of the score will be novelty. This will be judged based on the uniqueness of the solution methodology by a panel of expert judges.
- 30% of the score will be the quality of the final report and presentation. The final report will be graded based on organization, clearness of presentation, and detail of explanations. This will also be judged by a panel of expert judges.

 **Note that use of tools requiring a paid license or a demo license is not allowed**.


You can refer to the [deliverables section](logistics.md#deliverables) for more details on the qualification and final phase deliverables.


To find more information regarding how to register and participate click [here](logistics.md).
