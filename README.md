# Qats & DoQs
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4569383.svg)](https://doi.org/10.5281/zenodo.4569383)

[![Language grade: Python](https://img.shields.io/lgtm/grade/python/g/mickahell/quantum_data-classifier.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/mickahell/quantum_data-classifier/context:python)
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-5-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->

- Classifier of quantum cats and quantum dogs

## Structure <a name="structure"></a>
- Final script : `qats_doqs.ipynb`
- Folders :
	- datas : folder for the Qats and DoQs csv files
	- sensors : folder for the differents sensors (quantum generation)
	- classifiers : folder for the differents classifiers
	- combine : folder for the differents combining algorithms
	- training : folder for the differents training algorithms
	- graphs : folder for the differents graphs generation
	- communication : folder for images and ressources to present the project

## Idea <a name="idea"></a>
The classify regions of the Hilbert space. E.g. :
- An hemisphere of the Bloch sphere is _Qat_
- The other hemisphere is _doQ_

### First create quantum state with variational parameters
- As first step, we create a parameterized sensor that can create state vectors that fall either into the _cat_ or _dog_ region. (As black box)
	- We could use any other sensor with different parameterization as long as it's capable of producing _dog_ and _cat_ states.
- Then, we feed the output state of the sensor into a parameterized classifier circuit
- Then, we optimize the classifier
- Finally measure them and drawing graph

<pre>
        |----------|  |------------------------------------------------------|
	|  Sensor  |  |                    Processing                        |    
        | |------| |  | |-----------|                          |-----------| |      |---------|
        |-| S(x) |-|--|-| U<sub>1</sub>(θ<sub>1</sub>λ<sub>1</sub>ϕ<sub>1</sub>) |---------...---...--------| U<sub>m</sub>(θ<sub>m</sub>λ<sub>m</sub>ϕ<sub>m</sub>) |-|------| MEASURE |
        | |------| |  | |-----------|                          |-----------| |      |---------|
  	|----------|  |------------------------------------------------------|           |
  c0   ----------------------------------------------------------------------------------o-----
</pre>

#### Catch
- During operation, we cannot calculate expected values, because the sensor can run only once. So when we calculate the accuracy on the test set, we are not allowed to calculate expected values... we can run the circuit just once, make the PauliZ measurement, and if the result is "-1" we say "dog", if it's 1 we say "cat". (On the other hand, in the training phase we can optimize the circuit parameters, the thetas, using expected values of the measurements, as training is done in our laboratory. But operation may happen e.g. in a self-driving car.)

#### Compare with 
- The standard way of testing, that is, when we can run the circuit multiple times to get expected value of the PauliZ measurement :
	- The result can be e.g. 0.5, then we classify it as "cat", as it's closer to 1 than to -1. (So, you see that when we can run the circuit only once, we can be unlucky that we get -1, even if the expected value over many runs is 0.5.)

## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://github.com/saharbenrached"><img src="https://avatars.githubusercontent.com/u/58570811?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Sahar Ben Rached</b></sub></a><br /><a href="https://github.com/mickahell/qhack21/commits?author=saharbenrached" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/AlainChance"><img src="https://avatars.githubusercontent.com/u/43089974?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Alain</b></sub></a><br /><a href="https://github.com/mickahell/qhack21/commits?author=AlainChance" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/Zed-Is-Dead"><img src="https://avatars.githubusercontent.com/u/7906730?v=4?s=100" width="100px;" alt=""/><br /><sub><b>LQuerellaZ</b></sub></a><br /><a href="https://github.com/mickahell/qhack21/commits?author=Zed-Is-Dead" title="Code">💻</a></td>
    <td align="center"><a href="http://q-edu-lab.com"><img src="https://avatars.githubusercontent.com/u/72672758?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Tamás Varga</b></sub></a><br /><a href="https://github.com/mickahell/qhack21/commits?author=tvarga78" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/mickahell"><img src="https://avatars.githubusercontent.com/u/20951376?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Mica</b></sub></a><br /><a href="https://github.com/mickahell/qhack21/commits?author=mickahell" title="Code">💻</a></td>
  </tr>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!
