% Circular Convolution Using FFT
clc;
clear;

% Input sequences
x = [1, 2, 3, 4];  % Input signal
h = [1, 2, 1, 0];  % Impulse response

% Ensure both sequences are of the same length (zero-padding shorter one)
N = max(length(x), length(h));  % Circular convolution length
x = [x, zeros(1, N - length(x))];  % Zero-pad x
h = [h, zeros(1, N - length(h))];  % Zero-pad h

% Perform FFT on both sequences
X = fft(x);
H = fft(h);

% Multiply in the frequency domain
Y = X .* H;

% Perform inverse FFT to get the result
y = ifft(Y);

% Display results
disp('Input sequence (x):');
disp(x);
disp('Impulse response (h):');
disp(h);
disp('Circular Convolution Result (y):');
disp(real(y));  % Use real part (imaginary part is numerical noise)
