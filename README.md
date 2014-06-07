Introduction
============

OpenSSL and libcurl for Latest iOS.

Usage
=====

 1. Do "sh build-libraries.sh"
 2. Libraries are created at "lib".
 3. Copy libs and headers to your project.
 4. Import "libssl.a", "libcrypto.a", "libcurl.a".
 5. Reference Headers, "Headers/openssl", "Headers/curl".
 6. Specifying the flag  "-lz" in "Other Linker Flags" (OTHER_LDFLAGS) setting in the "Linking" section in the Build settings of the target.
 7. To use cURL, see below:

        #include <curl/curl.h>

        - (void)foo {    
            CURL* cURL = curl_easy_init();  
            ...  
        }

Updates
=======

22 Feb 2014
-----------
Xcode 5: Updated scripts to work with Xcode 5 and include new 64-bit targets (jasonacox)
	i386 	- iPhoneSimulator
	x86_64 	- iPhoneSimulator [new]
	armv7 	- iPhoneOS
	armv7s 	- iPhoneOS
	arm64 	- iPhoneOS [new]


7 Jun 2014
----------
Updated to use new OpenSSL version (1.0.1h).  Updated build scirpt to pull down latest cacert.pem.

NOTE:  To use the same libcurl header files for 32-bit and 64-bit targets, you need to add a buildtime condition to the curlbuild.h to define the sizeof(long):

	/* The size of `long', as computed by sizeof. */
	#ifdef __LP64__
	#define CURL_SIZEOF_LONG 8
	#else
	#define CURL_SIZEOF_LONG 4
	#endif

