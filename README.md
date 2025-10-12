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

<img width="995" height="785" alt="image" src="https://github.com/user-attachments/assets/4aa6a761-72d5-4f64-8f17-13bc101e6713" />

Open loop phase margin : 

<img width="991" height="776" alt="image" src="https://github.com/user-attachments/assets/65a76803-c92d-4e81-85d6-7f9ceabba722" />

## closed loop :

closed loop gain :

<img width="989" height="784" alt="image" src="https://github.com/user-attachments/assets/7bc6634f-cb50-4130-83ab-37a7ae991aec" />

closed  loop phase :

<img width="996" height="786" alt="image" src="https://github.com/user-attachments/assets/092006fa-a602-4fc2-91d5-f029f2979347" />

phase margin :

<img width="308" height="335" alt="image" src="https://github.com/user-attachments/assets/a424d7d8-54c7-4122-91bc-a014df1095d8" />

gain margin :

<img width="312" height="335" alt="image" src="https://github.com/user-attachments/assets/4d7bfe86-6359-4368-b88f-3443fb498512" />

loop gain :
<img width="994" height="777" alt="image" src="https://github.com/user-attachments/assets/4440897d-4a36-4650-8b5f-9230ad7348a9" />
## transient analysis :

<img width="983" height="782" alt="image" src="https://github.com/user-attachments/assets/bd89ac6a-72b0-49a2-b760-b8ca84d6e06d" />

slew rate :

<img width="642" height="774" alt="image" src="https://github.com/user-attachments/assets/f03c0d44-b5b1-4dc3-aa9b-bee6c9a9c0f1" />

 0.05 v/us ==> we need slew rate enhacement :)

 ## slew enhacement circuit :

 <img width="368" height="593" alt="image" src="https://github.com/user-attachments/assets/3cbc717c-74da-4e23-ae66-62c7b3a49daa" />

this circuit working flow:

at DC MP3 and MN3 are off.

at transient , at large signal MP3 and MN3 sense current change from the output

Case 1 — Output rising:

M7 (NMOS) conducts more (pulls output down normally).
​
increases → MN3 turns ON → adds extra sinking current → faster pull-down.

M7 + MN3 together sink more current than M7 alone.

Case 2 — Output falling:

M8 (PMOS) conducts more (pulls output up normally).

decreases → MP3 turns ON → adds extra sourcing current → faster pull-up.

<img width="1458" height="673" alt="image" src="https://github.com/user-attachments/assets/a58c7503-fd27-465f-8798-9657b2081c47" />


M8 + MP3 together source more current than M8 alone.
