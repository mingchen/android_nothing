DEMO
====

Empty project, only for demo purpose.


The debug keystore must have the same key alias and password as the ones that the Android build system generates, 
i.e. alias androiddebugkey, password android.

You can use keytool to generate a key with these properties:

    keytool -genkey -v -keyalg RSA -keysize 2048 -validity 10000 \
      -dname 'CN=Android Debug,O=Android,C=US' -keystore debug.keystore \
      -storepass android -alias androiddebugkey -keypass android


