import numpy as np
import matplotlib.pyplot as plt
import h5py
f = 'Datalog - 2014 06 13, Fri, 02-21-01.h5'
d = h5py.File(f)
spec_size = len(d['Spectrum_Data'][0,4:])
sum_intensities = {}
num_intensities = {}
for s in range(len(d['Spectrum_Data'][:,1])):
    freqs = np.arange(spec_size) * d['Spectrum_Data'][s,2] + d['Spectrum_Data'][s,1]
    intensities = d['Spectrum_Data'][s,4:]
    for i in range(spec_size):
        freq = freqs[i]
        sum_intensities[freq] = sum_intensities.get(freq, 0) + intensities[i]
        num_intensities[freq] = num_intensities.get(freq, 0) + 1
freqs = np.array(sorted(sum_intensities.keys()))
np_sum_intensities = np.array([sum_intensities[x] for x in freqs])
np_num_intensities = np.array([num_intensities[x] for x in freqs])
avg_intensities = np_sum_intensities / np_num_intensities
result = np.transpose(np.array([freqs, avg_intensities]))
x = [i[0] for i in result]
y = [i[1] for i in result]
figure()
xlabel('Frequency (Hz)')
ylabel('Intensity')
title('Intensity vs. Frequency (Hz)')
plt.plot(x, y,'r')
savefig('i-f_graph.png')
plt.show()
