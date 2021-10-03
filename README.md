# Raspi-RTCmo-build

git clone https://github.com/raspberrypi/tools ~/raspi/tools

echo PATH=$PATH:~/raspi/tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian/bin >> ~/.bashrc source ~/.bashrc
echo PATH=\$PATH:~/raspi/tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian-x64/bin >> ~/.bashrc source ~/.bashrc

# Linux 4.19.75-v7+
git checkout fe915debc1925397f78db8bbfc9f488b0ce4e009

nano Makefile

# For Pi2, Pi3, Pi3+ or CM3
KERNEL=kernel7
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2709_defconfig

make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- menuconfig

# Navigate to Driver - Real time clock - RTC-RV8803 and set "M". Safe all


cp ~/raspi/linux/drivers/rtc/rtc-rv8803.ko ~/raspi/export/drivers/rtc/rtc-rv8803.ko
