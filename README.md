# fft-ts
A TypeScript library to operate a Cooley-Tukey FFT.

![Sample](https://github.com/tatsuky/fft-ts/blob/master/images/sample.png)

## Getting Started
```ts
import { Complex } from './complex';
import { FFT } from './fft';
```

```ts
const fft = FFT();
```

## Applying a FFT
For `Complex` usage, see [tatsuky/complex-ts](https://github.com/tatsuky/complex-ts/).

### 1D
```ts
const data: Complex[] = someFunctionToLoad1DData();
const size = data.length;
const spectrum = fft.fft1d(data, size);

// max is to normalize power spectrum data.
const [powerSpectrum, max] = fft.power1d(spectrum, size);
```

### 2D
```ts
const data: Complex[][] = someFunctionToLoad2DData();
const [width, height] = [data[0].length, data.length];

let spectrum = fft.fft2d(data, width, height);
spectrum = fft.shift(spectrum, width, height);

// max is to normalize power spectrum data.
const [powerSpectrum, max] = fft.power2d(powerSpectrum, width, height);
```

## Applying an IFFT
### 1D
```ts
const data = fft.ifft1d(spectrum, size);
```

### 2D
```ts
const data = fft.ifft2d(spectrum, width, height);
```

## Notes
Since FFTs in this library is not optimized, the execution speed might be slower than the commercial FFT libraries. This library is suitable for educational or experimental purposes only.
