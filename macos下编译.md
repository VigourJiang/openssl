# 在Mac下编译
./config 
make -j4



# 执行命令
## 查看版本号
        $ DYLD_LIBRARY_PATH=$(pwd) ./apps/openssl version
        OpenSSL 1.1.2-dev  xx XXX xxxx
## 验证内置了SM2曲线
        $ DYLD_LIBRARY_PATH=$(pwd) ./apps/openssl ecparam -list_curves | grep SM2
        SM2       : SM2 curve over a 256 bit prime field
## 生成一对SM2公私钥
        $ DYLD_LIBRARY_PATH=$(pwd) ./apps/openssl ecparam -genkey  -name SM2 -out eckey.pem -text

## 查看生成的SM2公私钥
        $ DYLD_LIBRARY_PATH=$(pwd) ./apps/openssl ec -text -in eckey.pem
        read EC key
        Private-Key: (256 bit)
        priv:
            7d:12:2c:83:df:ab:37:c7:d6:ca:c3:7a:31:fa:11:
            46:65:9a:ea:b9:79:37:cc:2f:56:f1:22:bb:e3:a6:
            44:19
        pub:
            04:57:f3:cd:0e:98:c1:40:1c:ac:d5:3d:b8:5b:3c:
            b5:8b:d6:33:b8:f3:c8:6e:c7:79:f6:a4:e0:48:cc:
            37:2a:57:86:ee:2a:c0:60:7a:0a:44:95:7a:6e:02:
            95:8e:c7:f2:3c:91:ce:36:42:1a:f2:f2:cc:a8:20:
            1e:d1:bf:5d:db
        ASN1 OID: SM2
        writing EC key
        -----BEGIN EC PRIVATE KEY-----
        MHcCAQEEIH0SLIPfqzfH1srDejH6EUZlmuq5eTfML1bxIrvjpkQZoGCCqBHM9V
        AYItoUQDQgAEV/PNDpjBQBys1T24Wzy1i9YzuPPIbsd59qTgSMw3eG7irAYHoK
        RJV6bgKVjsfyPJHONkIa8vLMqCAe0b9d2w==
        -----END EC PRIVATE KEY-----