# Radar Jamming Resistance - Suppression of Jamming (Noise Frequency Modulation, AM Interference) - Includes MATLAB Code

\t MATLAB code
close all\nclear all\nwarning off\nfADC = 10e6; %sampling rate\nfCar = 4e6; %carrier frequency\nTtotal = 7.5e-6; %total time duration\nT = 5.5e-6; %signal duration\nA = 1; %signal amplitude\nnum_jam = 2;\nt = 0:1/fADC:T - 1/fADC; %signal time\n​\ntTotal = 0:1/fADC:Ttotal - 1/fADC; %time axis\n​\nNspace = round((Ttotal - T)*fADC/2); %points of time without signal\n​\n%Generate MP signal\nsigMP = A*exp(j*2*pi*fCar*t);    %Generate the MP signal\nsigMP = [zeros(1,Nspace),sigMP, zeros(1,Nspace)];\n​\n%Generate BPSK signal (11 bit Barker code)\nLen = length(t);\nNcode = 11;\nfor kIndex = 1:Len\n    if kIndex<Len/Ncode\n        sBPSK(kIndex)=1;\n    elseif kIndex<Len/Ncode*2\n        sBPSK(kIndex)=1;\n    elseif kIndex<Len/Ncode*3\n        sBPSK(kIndex)=1;\n    elseif kIndex<Len/Ncode*4\n        sBPSK(kIndex)=-1;\n    elseif kIndex<Len/Ncode*5\n        sBPSK(kIndex)=-1;\n    elseif kIndex<Len/Ncode*6\n        sBPSK(kIndex)=-1;\n    elseif kIndex<Len/Ncode*7\n        sBPSK(kIndex)=1;\n    elseif kIndex<Len/Ncode*8\n        sBPSK(kIndex)=-1;\n    elseif kIndex<Len/Ncode*9\n        sBPSK(kIndex)=-1;\n    elseif kIndex<Len/Ncode*10\n        sBPSK(kIndex)=1;\n    else\n        sBPSK(kIndex)=-1;\n    end\nend\nsMP = A*exp(j*2*pi*fCar*t);    %Generate the MP signal\nsigBPSK = sMP.*sBPSK;\nsigBPSK = [zeros(1,Nspace),sigBPSK, zeros(1,Nspace)];\n​\n%Generate LFM signal\nB = 4e6;\nchirpRate =B/Ttotal;\nsigLFM = A*exp(j*2*pi*fCar*t + j*pi*chirpRate*t.^2);\nsigLFM = [zeros(1,Nspace),sigLFM, zeros(1,Nspace)];\n​\n%Generate NLFM signal\na1 = 1e11;\na2 = 5e16;\nsigNLFM = A*exp(j*2*pi*fCar*t + j*pi*a1*t.^2 + j*pi*a2*t.^3);\nsigNLFM = [zeros(1,Nspace),sigNLFM, zeros(1,Nspace)];\n​\n%Input signal\nsig = sigLFM;%change signal type for different input\nfigure;\nplot(tTotal*1e6,sig)\nxlabel('t/us')\nylabel('Amplitude')\n​\nsig = awgn(sig,1000,'measured');\nfigure;\nplot(tTotal*1e6,sig)\nxlabel('t/us')\nylabel('Amplitude')\ntitle('Undisturbed echo waveform in time domain')\n​  

## Images

![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](01.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](02.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](03.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](04.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](05.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](06.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](07.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](08.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](09.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](10.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](11.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](12.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](13.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](14.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](15.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](16.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](17.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](18.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](19.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](20.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](21.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](22.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](23.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](24.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](25.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](26.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](27.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](28.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](29.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](30.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](31.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](32.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](33.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](34.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](35.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](36.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](37.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](38.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](39.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](40.jpg)
![(Radar Interference)Suppressing interference (noise frequency modulation, amplitude modulation interference) suppression [Attached MATLAB code]](41.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
