# Description
This project is tailored for bare-metal software development, enabling you to write code for embedded systems based on the STM32 microcontroller without the need to install toolchaines or make tools in your system. The cross-compiler toolchain is customizable, allowing you to optimize performance and memory usage for your specific hardware requirements. Join our community of developers to explore the possibilities of bare-metal programming and adapt this project to suit your unique needs.

# Requirements

Before running this project, make sure you have the following installed:
- git
- docker


# Clone the repo and choose your template 
```
git clone https://github.com/hdfixi/CrossCompilerProject.git
```
```
cd CrossCompilerProject

```
chosse the template for your card 
```
git clone git@github.com:STM32-base/STM32-base-F0-template.git
git clone git@github.com:STM32-base/STM32-base-F1-template.git
git clone git@github.com:STM32-base/STM32-base-F2-template.git
git clone git@github.com:STM32-base/STM32-base-F3-template.git
git clone git@github.com:STM32-base/STM32-base-F4-template.git
git clone git@github.com:STM32-base/STM32-base-F7-template.git
```
then link the STM32-base and the STM32-base-STM32Cube
```
ln -s ../STM32-base
```
```
ln -s ../STM32-base-STM32Cube

```
# Costume your code 
navigate to STM32-base templated you have just cloned 
for exemple 
```
cd STM32-base-F4-template/src
```
now you can edit the main.c file 
# Run & Compile your code 
first of all you need to run the container which contained the needs tool-chaines 

## To run the container you have two options 

### Create the docker image by yourself than run it 
create the image 
```
cd DockerImage
```
```
docker build -t stm32-cross-compiler .                                                         
```
Now we are going to run the container and mount it to our local project 
```
cd .. 
```
```
docker run --rm -it -v $(pwd)/STM32-project:/project stm32-cross-compiler
```
if you faced some permission errors try to add a sudo 
### Or directly pull it from Docker-Hub 
```
docker run --rm -it -v $(pwd)/STM32-project:/project hdfixi/stm32-cross-compiler
```
## To compile & create the firmware
in your container terminal navigate to /project
```
cd project
``` 
than the template directory for exemple
```
cd STM32-base-F4-template
```
than 
```
make
```
the generated firmware will be located in STM32-base-F4-template/bin

You can use any tool to flash it into your card such as ST-link tools 
