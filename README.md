# three_stage_ota
in this repo we will design a three stage ota using 22nm fdsoi and we will use this paper as a refernce for this project :
we will learn some concept like cascaded stages, miller compensation. 

we will start by sizing th SE folded cascode:

<img width="756" height="439" alt="image" src="https://github.com/user-attachments/assets/36c540a6-4ab8-42bd-9dee-7a1b81f89ac7" />

folded cascode after sizing :

<img width="1634" height="645" alt="image" src="https://github.com/user-attachments/assets/f9b32ffd-b12b-4c9f-b05d-b94160ac6ec8" />

Sizing steps :

1) we have three stages so i try to divide the gain requirement for each i assumed that i will try to get a gain of 60 - 70 db from the first stage  
i assumed that i have a slew rate of 10v/us ==> Iss/Cl and adding a margin for parasetic caps we assume a CL of 1.2p farad so calculating Iss i get a current of 6u in each branch so a total of 12uA.
2) we have a GBW of 5Mhz so we can get GBW=gm1/2*pi*CL ==> gm1 =31.46usiemens ==> so gm1/id = 5.2 so gm/id > 5.2 is good for a first stage.
3) I assumed vds of 400m on input and 200m on current mirroir and nmos bias part M4.

<img width="497" height="360" alt="image" src="https://github.com/user-attachments/assets/1d874c03-3354-49ee-8604-016465823700" />

test bench ==> remeber better to put drain and source voltage in that configuration so we get a more accurate Vth from the simulation and higher accuracy after design.

<img width="1619" height="756" alt="image" src="https://github.com/user-attachments/assets/a19c30f0-0520-44a2-af4d-9dec9948bafa" />

4)  from here we can assume multpile transistor gain and gds that will help us in our design.


## biasing network :

<img width="371" height="212" alt="image" src="https://github.com/user-attachments/assets/a4235cc7-aaa9-4eb1-a269-cf3e170450ac" />

## 2 stages :

<img width="752" height="532" alt="image" src="https://github.com/user-attachments/assets/14de6d36-157f-437b-8cea-f610491deda3" />

AOL and unity gain frequency:

<img width="995" height="790" alt="image" src="https://github.com/user-attachments/assets/960893b5-90b9-452e-a60d-012f73bbfc40" />

CMIR:

<img width="1000" height="785" alt="image" src="https://github.com/user-attachments/assets/9ac68efc-14af-4099-9205-001d2f7a359c" />


