* mkdir -pv <my_working_dir>/mydroid && cd <my_working_dir>/mydroid
* repo init -u https://android.googlesource.com/platform/manifest -b android-14.0.0_r45 --depth=1
* curl -o .repo/local_manifests/local_manifest.xml -L https://raw.githubusercontent.com/kyndytran/android_manifest/android14/local_manifest.xml --create-dirs
* repo sync
