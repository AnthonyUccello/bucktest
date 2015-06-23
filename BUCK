android_binary(
  name = 'pumpup',
  manifest = 'AndroidManifest.xml',
  keystore = ':debug_keystore',
  deps = [
    ':res',
    ':all-jars',
    ':src',
  ],
)

android_resource(
  name = 'res',
  res = 'res',
  assets = 'assets',
  manifest = 'AndroidManifest.xml',
)

import re

jar_deps = []
for jarfile in glob(['libs/**/*.jar']):
  name = 'jars__' + re.sub(r'^.*/([^/]+)\.jar$', r'\1', jarfile)
  jar_deps.append(':' + name)
  prebuilt_jar(
    name = name,
    binary_jar = jarfile,
  )

android_library(
  name = 'all-jars',
  exported_deps = jar_deps,
)

android_library(
  name = 'src',
  srcs = glob(['*.java']),
  deps = [
    ':res',
  ],
)

keystore(
  name = 'debug_keystore',
  store = 'debug.keystore',
  properties = 'debug.keystore.properties',
)