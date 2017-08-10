# Node-Webrtc-Native

This module is mainly the code of [webrtc-native] but the webrtc.node binary is built using script used in [node-webrtc]. That was useful to be as [node-webrtc] uses [build-webrtc] to compile the code and extract headers, and I find this handy.

The code contains another extra sample for one way video broadcast that works from the first time :)

To build the code you can follow these [installation-steps] it is straight forward. in case you find issue check the below tricks.

## Building Webrtc Tricks
 -  XOpenDisplay : some times you have this [XOpenDisplay-issue] and then you need to set (include_pulse_audio=0 and include_internal_video_render=0) in jakelib/environment.js in [build-webrtc] module as follows:
```sh
var GYP_DEFINES = [
  'target_arch=' + ARCH,
  'host_arch=' + os.arch(),
  'build_with_chromium=0',
  'use_openssl=0',
  'use_gtk=0',
  'use_x11=0',
  'include_examples=0',
  'include_tests=1',  
  'include_pulse_audio=0',
  'include_internal_video_render=0',
  'fastbuild=1',
  'remove_webcore_debug_symbols=1'
];
```

 - Node v6 gives warning when using it in building webrtc.node module. Node v8 gives errors. Use node version < 6.0
 - You may find a lost jsoncpp library. Please install
 ```sh
sudo apt-get install libjsoncpp-dev
ln -s /usr/include/jsoncpp/json /usr/include/json
 ```
 - [ERROR: webrtc-native@1.4.0~install: cannot run in wd %s %s (wd=%s) webrtc-native@1.4.0 node-pre-gyp install     --fallback-to-build /mnt/vdb/webrtc-native] just add --unsafe-perm 
 ```sh
sudo apt-get install libjsoncpp-dev
npm install --build-from-source --unsafe-perm
 ```

License
----

MIT


**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)
   [XOpenDisplay-issue]: <https://github.com/js-platform/node-webrtc/issues/281> 
   [installation-steps]: <https://github.com/js-platform/node-webrtc/wiki/Building>
   [build-webrtc]: <https://github.com/markandrus/build-webrtc>
   [webrtc-native]: <https://github.com/vmolsa/webrtc-native>
   [node-webrtc]: <https://github.com/js-platform/node-webrtc>
   
