# FIR-FILTER-DESIGN
# EXP 4 c: Design-of-FIR-Digital-Filter-using-Hanning-Window

# AIM 1:  To perform Design-of-LOWPASS FIR-Digital-Filter-using-Hanning-Window using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc;
clear;
close;

// Input Parameters
M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off Frequency = ');

alpha = (M - 1)/2;    // Center Value

// Ideal LPF Coefficients
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = Wc / %pi;
    else
        hd(n) = sin(Wc * ((n - 1) - alpha)) / (((n - 1) - alpha) * %pi);
    end
end

// Hanning Window
for n = 1:M
    W(n) = 0.5 - 0.5 * cos((2 * %pi * (n - 1)) / (M - 1));
end

// Windowed Filter Coefficients
h = hd .* W;

disp(h, 'Filter Coefficients are');

// Frequency Response
[hzm, fr] = frmag(h, 256);

// Magnitude Response
subplot(2,1,1);
plot(2 * fr, hzm);
xlabel('Normalized Digital Frequency (\omega)');
ylabel('Magnitude');
title('Frequency Response of FIR LPF using Hanning Window');

// Magnitude in dB
hzm_dB = 20 * log10(hzm);

subplot(2,1,2);
plot(2 * fr, hzm_dB);
xlabel('Normalized Digital Frequency (\omega)');
ylabel('Magnitude in dB');
title('Frequency Response of FIR LPF using Hanning Window');

```

# OUTPUT: 

<img width="757" height="712" alt="image" src="https://github.com/user-attachments/assets/0884b3fb-d36c-4858-b807-ff7a21b0fc09" />
<img width="895" height="992" alt="image" src="https://github.com/user-attachments/assets/e1d0c7cb-1026-445f-8f74-327b6b1a072f" />

# MANUAL CALCULATION:
<img width="987" height="1600" alt="image" src="https://github.com/user-attachments/assets/a2c02eef-3f8e-4e31-9960-f32db2264922" />

<img width="1440" height="1600" alt="image" src="https://github.com/user-attachments/assets/af400e2a-966f-4358-afc4-a83692eaa807" />


# RESULT: 

Thus design of low pass FIR digital filter using-Hanning-Window waveforms were plotted and output was verified.

# AIM 2: To perform DESIGN OF HIGH PASS FIR DIGITAL FILTERS using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc;
clear;
close;

// Input Parameters
M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off Frequency = ');

alpha = (M - 1)/2;    // Center Value

// Ideal HPF Coefficients
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = 1 - Wc/%pi;
    else
        hd(n) = -sin(Wc*((n-1)-alpha))/(((n-1)-alpha)*%pi);
    end
end

// Hanning Window
for n = 1:M
    W(n) = 0.5 - (0.5*cos((2*%pi*(n-1))/(M-1)));
end

// Windowing Filter Coefficients
h = hd .* W;

disp(h,'Filter Coefficients are');

// Frequency Response
[hzm,fr] = frmag(h,256);

// Magnitude Response
subplot(2,1,1);
plot(2*fr,hzm);
xlabel('Normalized Digital Frequency (\omega)');
ylabel('Magnitude');
title('Frequency Response of FIR HPF using Hanning Window');

// Magnitude Response in dB
hzm_dB = 20*log10(hzm);

subplot(2,1,2);
plot(2*fr,hzm_dB);
xlabel('Normalized Digital Frequency (\omega)');
ylabel('Magnitude in dB');
title('Frequency Response of FIR HPF using Hanning Window');
```


# OUTPUT: 
<img width="752" height="717" alt="image" src="https://github.com/user-attachments/assets/8ee72a5f-5e87-4c28-a120-8515457214b0" />
<img width="531" height="612" alt="image" src="https://github.com/user-attachments/assets/9bca9aec-7592-47fa-96e1-0e13d134130a" />


# RESULT: 
Thus design of HIGH pass FIR digital filter using-Hanning-Window waveforms were plotted and output was verified.

# AIM 3: To perform DESIGN OF BAND PASS FIR DIGITAL FILTERS using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc;
clear;
close;

// Input Parameters
M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cutoff Frequencies [Wc1 Wc2] = ');

Wc1 = Wc(1);
Wc2 = Wc(2);

alpha = (M - 1)/2;     // Center Value

// Ideal BPF Coefficients
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = (Wc2 - Wc1)/%pi;
    else
        hd(n) = (sin(Wc2*((n-1)-alpha)) - sin(Wc1*((n-1)-alpha))) ...
                / (((n-1)-alpha)*%pi);
    end
end

// Hanning Window
for n = 1:M
    W(n) = 0.5 - 0.5*cos((2*%pi*(n-1))/(M-1));
end

// Windowing Filter Coefficients
h = hd .* W;

disp(h,'Filter Coefficients are');

// Frequency Response
[hzm,fr] = frmag(h,256);

// Magnitude Response
subplot(2,1,1);
plot(2*fr,hzm);
xlabel('Normalized Digital Frequency (\omega)');
ylabel('Magnitude');
title('Frequency Response of FIR BPF using Hanning Window');

// Magnitude Response in dB
hzm_dB = 20*log10(hzm);

subplot(2,1,2);
plot(2*fr,hzm_dB);
xlabel('Normalized Digital Frequency (\omega)');
ylabel('Magnitude in dB');
title('Frequency Response of FIR BPF using Hanning Window');
```


# OUTPUT: 

<img width="758" height="717" alt="image" src="https://github.com/user-attachments/assets/cf31b60a-1da1-455c-a0ce-4831e49c0013" />
<img width="717" height="631" alt="image" src="https://github.com/user-attachments/assets/799e0dcb-f17a-4cdf-8d60-dba20a299ce9" />

# RESULT: 
Thus design of BAND pass FIR digital filter using-Hanning-Window waveforms were plotted and output was verified.

# AIM 4: To perform DESIGN OF BAND STOP FIR DIGITAL FILTER using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 

```
clc;
clear;
close;

// Input Parameters
M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cutoff Frequencies [Wc1 Wc2] = ');

Wc1 = Wc(1);
Wc2 = Wc(2);

alpha = (M - 1)/2;     // Center Value

// Ideal BSF Coefficients
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = 1 - ((Wc2 - Wc1)/%pi);
    else
        hd(n) = (sin(Wc1*((n-1)-alpha)) - sin(Wc2*((n-1)-alpha))) ...
                / (((n-1)-alpha)*%pi);
    end
end

// Hanning Window
for n = 1:M
    W(n) = 0.5 - 0.5*cos((2*%pi*(n-1))/(M-1));
end

// Windowing Filter Coefficients
h = hd .* W;

disp(h,'Filter Coefficients are');

// Frequency Response
[hzm,fr] = frmag(h,256);

// Magnitude Response
subplot(2,1,1);
plot(2*fr,hzm);
xlabel('Normalized Digital Frequency (\omega)');
ylabel('Magnitude');
title('Frequency Response of FIR BSF using Hanning Window');

// Magnitude Response in dB
hzm_dB = 20*log10(hzm);

subplot(2,1,2);
plot(2*fr,hzm_dB);
xlabel('Normalized Digital Frequency (\omega)');
ylabel('Magnitude in dB');
title('Frequency Response of FIR BSF using Hanning Window');
```
# OUTPUT: 

<img width="755" height="722" alt="image" src="https://github.com/user-attachments/assets/25d076a1-a2e0-4818-824e-a20a76abe231" />
<img width="721" height="695" alt="image" src="https://github.com/user-attachments/assets/c013e017-b999-497e-8dc8-e5d5608394c4" />

# RESULT: 
Thus design of BAND STOP FIR digital filter using-Hanning-Window waveforms were plotted and output was verified.
