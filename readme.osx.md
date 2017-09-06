##build

./autogen.sh && chmod +x nomacro.pl && cd asm && ../nomacro.pl && cd ..
./configure --with-curl --with-crypto=/usr/local/opt/openssl CFLAGS="-march=native"
perl -p -i -e "s/#if \(WINDOWS\)/#define ASM 0\n#if (WINDOWS)/g" algo/neoscrypt.c
make
