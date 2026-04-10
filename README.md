README

1. SCHEMATIC
În prima parte a proiectului am avut de realizat schema electrică a smartwatch-ului pornind de la modelul oferit pe OCW. Am folosit exclusiv biblioteca de componente pusă la dispoziție în cadrul proiectului, pentru a păstra footprint-urile și simbolurile conforme cu cerințele.
Am început prin a plasa în schematic toate blocurile funcționale principale ale dispozitivului:
•	LiPo Charger 
•	DC/DC 
•	IMU 
•	SWD 
•	E-Paper Drive Circuit 
•	E-Paper Display Connector 
•	Haptic Driver 
•	Fuel Gauge 
•	Buttons 
•	USB C Connector & ESD Protection 
După plasarea componentelor, am trecut la realizarea conexiunilor dintre ele și microcontroller, urmărind schema de referință și datasheet-urile componentelor importante.
În procesul de realizare a schemei a trebuit să:
•	modific valorile unor rezistențe și condensatoare pentru a corespunde cerințelor din modelul de referință; 
•	aleg capsulele corecte pentru componentele pasive, conform regulilor proiectului; 
•	adaug condensatoare de decuplare pe liniile de alimentare pentru circuitele integrate; 
•	completez valorile și denumirile componentelor pasive; 
•	adaug net labels pentru semnalele importante, astfel încât schema să fie mai clară și conexiunile să poată fi urmărite mai ușor; 
•	etichetez liniile de alimentare și semnalele de comunicație; 
•	organizez schematicul pe blocuri funcționale pentru a separa partea de power, senzori, display și debugging. 
O parte importantă a procesului a fost verificarea atentă a pinilor fiecărei componente și corelarea lor cu semnalele din schema de referință. Am urmărit în special liniile de alimentare, comunicația I2C/SPI, liniile SWD și conexiunile către display.
La final am verificat schema pentru a mă asigura că toate componentele sunt conectate corect și că structura este pregătită pentru etapa de PCB layout.
2. PCB DESIGN
După ce am terminat schema, am trecut la realizarea PCB-ului folosind dimensiunile recomandate din fișierul mecanic.
Mai întâi am făcut placement-ul componentelor pe layer-ul TOP, respectând cât am putut layout-ul recomandat. Am poziționat componentele principale, cum ar fi microcontrollerul, circuitul de încărcare, convertorul DC/DC, IMU-ul, driverul haptic, fuel gauge-ul, conectorul pentru display, USB-C și butoanele.
După aceea am plasat componentele pasive în jurul circuitelor integrate, mai ales condensatoarele de decuplare și filtrare, cât mai aproape de pinii de alimentare.
Următorul pas a fost rutarea traseelor, unde am separat traseele de alimentare de cele de semnal și am folosit plane de masă pe TOP și BOTTOM. Am avut grijă să păstrez zona antenei liberă și să aliniez corect butoanele și mufa USB cu carcasa.
La final am verificat designul cu DRC, am corectat erorile principale și am generat modelul 3D pentru a verifica dacă PCB-ul se integrează corect în carcasa smartwatch-ului.
3. 3D MODEL
După finalizarea PCB-ului, am realizat modelul 3D al ansamblului pentru a verifica integrarea componentelor în carcasă.
Am inclus PCB-ul, bateria, display-ul și carcasa, iar apoi am verificat poziționarea acestora astfel încât să nu existe suprapuneri și să fie aliniate corect butoanele și portul USB-C.
La final am exportat modelul în format STEP, pentru a putea fi folosit la verificarea mecanică și la prezentarea finală a proiectului.
