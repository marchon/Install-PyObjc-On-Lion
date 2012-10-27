The Problem. 
============================================ 
pip doesn't install PyObjC


The Solution 
============================================ 
virtualenv env # setup the virtual env
source env/bin/activate
pip install pyobjc
#now it fails with pyobjc-core
# 1: update some permissions
chmod a+x env/build/pyobjc-core/libxml2-src/configure
chmod a+x env/build/pyobjc-core/libxml2-src/install-sh
# 2: do some find/replace
sed -i.bak 's/use_2to3 = True/use_2to3 = False/g' env/build/pyobjc-core/setup.py
# 3: install with the setup.py
pushd env/build/pyobjc-core/
python setup.py install
popd
# 4: retry the pyobjc install
pip install pyobjc


source of solution... 

https://github.com/pypa/pip/issues/11

