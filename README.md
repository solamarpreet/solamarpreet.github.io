<div id="top"></div>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![GPLv3 License][license-shield]][license-url]
[![Last Commit][last-commit-shield]][last-commit-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">
<a href="https://solamarpreet.github.io">
    <img src="static/solpic.jpeg" alt="Logo" width="125" height="125">
  </a>
<h2 align="center">solamarpreet.github.io</h2>

  <p align="center">
    <i>This repo contains the code used to generate my Blog & Portfolio</i>
    <br />
  </p>
</div>
<br />


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#troubleshooting">Troubleshooting</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>
<br />


<!-- GETTING STARTED -->
## Getting Started

This guide assumes you are looking to setup a working environment that can generate a local copy of the website hosted at [solamarpreet.github.io](https://solamarpreet.github.io) which you can then modify to suit your needs.

### Prerequisites

The following external dependencies need to be pre-installed
* [Hugo](https://gohugo.io/getting-started/installing/)
<br />

### Installation

1. Clone the repo and cd into the folder
   ```sh
   git clone https://github.com/solamarpreet/solamarpreet.github.io.git && cd solamarpreet.github.io
   ```
2. Download the theme submodule required by the project 
   ```sh
   git submodule update --init --recursive
   ```
> **Note**: You will need to manually update the submodules if the theme changes upstream as git pull wont automatically do that for you
>
> ```sh
> git submodule update --remote --merge
> ```
3. Start the Hugo development server
   ```sh
   hugo server -D
   ```
4. Generate the static HTML files by simply running the hugo command. Files will appear in the **/public** folder
   ```sh
   hugo
   ```
<br />


<!-- TROUBLESHOOTING -->
## Troubleshooting

If your changes are not reflected correctly by the live development server try restarting the server.

If that does not help address your issue check the [open issues](https://github.com/solamarpreet/solamarpreet.github.io/issues) for a list of known issues and open a new issue. Additionally check theme related issues at [PaperMod](https://github.com/adityatelange/hugo-PaperMod/issues).

<br />


<!-- CONTRIBUTING -->
## Contributing

If you have a suggestion regarding the website or wish to see some specific content on the blog simply open an issue with the tag "suggestion". You can also fork the repo, add your code and create a pull request.

<br />

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.

<br />

<!-- CONTACT -->
## Contact

Amarpreet Singh - solamarpreet@protonmail.com

Blog & Portfolio : [https://solamarpreet.github.io](https://solamarpreet.github.io)

<br />

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [PaperMod Project](https://github.com/adityatelange/hugo-PaperMod)
* [othneildrew](https://github.com/othneildrew/Best-README-Template)

<br />
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/solamarpreet/solamarpreet.github.io.svg?style=for-the-badge
[contributors-url]: https://github.com/solamarpreet/solamarpreet.github.io/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/solamarpreet/solamarpreet.github.io.svg?style=for-the-badge
[forks-url]: https://github.com/solamarpreet/solamarpreet.github.io/network/members
[stars-shield]: https://img.shields.io/github/stars/solamarpreet/solamarpreet.github.io.svg?style=for-the-badge
[stars-url]: https://github.com/solamarpreet/solamarpreet.github.io/stargazers
[issues-shield]: https://img.shields.io/github/issues/solamarpreet/solamarpreet.github.io.svg?style=for-the-badge
[issues-url]: https://github.com/solamarpreet/solamarpreet.github.io/issues
[license-shield]: https://img.shields.io/github/license/solamarpreet/solamarpreet.github.io.svg?style=for-the-badge
[license-url]: https://github.com/solamarpreet/solamarpreet.github.io/blob/main/LICENSE
[last-commit-shield]: https://img.shields.io/github/last-commit/solamarpreet/solamarpreet.github.io?style=for-the-badge
[last-commit-url]: https://github.com/solamarpreet/solamarpreet.github.io/pulse
