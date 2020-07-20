# Test install ARI and AWS Polly on MacOS
Artificially generated voice for tutorials/talks

Saw a talk at [BCC2020](https://bcc2020.github.io/) with an artificially generated voice, to make writing tutorials scriptable. I'm checking ease of installation. Pretty easy to install on MacOS v10.13.6 :)

Please cite the original [jhudsl/ari](https://github.com/jhudsl/ari) repo. 

* Sean Kross (2020). ari: Automated R Instructor. R package version 0.3.5. [https://CRAN.R-project.org/package=ari](https://cran.r-project.org/web/packages/ari/index.html)

## Begin Test

<details><summary>(1) Install on MacOS - <b>DONE</b></summary>

In R

```
# Install packages
install.packages(c("ari", "aws.polly"))

library(ari)
library(aws.polly)
# You will need an AWS instance with key (see security section/key generation)
Sys.setenv("AWS_ACCESS_KEY_ID" = "paste your key here",
           "AWS_SECRET_ACCESS_KEY" = "paste other key here",
           "AWS_DEFAULT_REGION" = "us-east-2")
```

In bash, install `ffmpeg`. I used homebrew package manager.

```
brew install ffmpeg
```

</details>

<details><summary>(2) Create an example video - <b>DONE</b></summary>

An example talk is converted to video `jen_example.Rmd`. 

In R

```
ari_narrate(
  "talk/jen_example.Rmd",
  "talk/jen_example.html",
  voice = "Kendra",
  delay = 0.5,
  capture_method = "iterative")
```

In bash... for some reason the generated video is not in current directory

```
# The path name is printed in R
mv /private/var/folders/wt/gw5b79wn4sjcpny6d0x4p1680000gn/T/RtmpQCS9pF/file10a1b28a86c6f.mp4 .
mv file10a1b28a86c6f.mp4 jen_example.mp4    # rename it
```
</details>

Finish: [See Ari Generated Video](talk/jen_example.mp4). : )
