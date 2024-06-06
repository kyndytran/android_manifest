*1. Download and sync source*
* mkdir -pv <my_working_dir>/mydroid && cd <my_working_dir>/mydroid
* repo init -u https://android.googlesource.com/platform/manifest -b android-14.0.0_r45 --depth=1
* curl -o .repo/local_manifests/local_manifest.xml -L https://raw.githubusercontent.com/kyndytran/android_manifest/android14/local_manifest.xml --create-dirs
* repo sync

*2. Tips for saving build time for next build with ccache (only do below steps at the first Android build time)*
* sudo apt-get install -y ccache
* export USE_CCACHE=1
* mkdir -pv <my_working_dir>/MYCCACHE_DIR (Create the folder on the disk which has more than 50GB available to use ccache)
* export CCACHE_DIR=<my_working_dir>/MYCCACHE_DIR/ (Update <my_working_dir> by your real path)
* export CCACHE_EXEC=/usr/bin/ccache
* ccache -M 50G


*3. Tips for building Android 14 AOSP with low RAM PC (my case: RAM 32GB, Swap 30GB, Android AOSP build thread is killed)*

Android AOSP only consumes much memory when performing first build or update *.bp files to create build/soong files.

1. Increase swap from 30 GB to 50GB. Refer: https://askubuntu.com/questions/178712/how-to-increase-swap-space (Use sudo)
2. Change heap configuration to metalava. Refer: https://github.com/verNANDo57/android_build_soong/commit/ffc8846a01fcfc20d6cf8ca701ef73d99f15acad
3. Set Java heap (put to ~/.bashrc. So that you don't need to re-run next time): export _JAVA_OPTIONS="-Xmx16g"
