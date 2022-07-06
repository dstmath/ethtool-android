cmake_minimum_required(VERSION 3.18.4)
project(ethtool C)

set(CMAKE_C_STANDARD 99)
#set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-missing-field-initializers -Wmacro-redefined")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-missing-field-initializers -Wbuiltin-macro-redefined")
include_directories(ethtool-5.18/uapi/)
#link_directories(ethtool-5.18)
set(ethtool_sources
        amd8111e.c
        at76c50x-usb.c
        de2104x.c
        dsa.c
        e100.c
        e1000.c
        et131x.c
        ethtool.c
        fec.c
        fec_8xx.c
        fjes.c
        ibm_emac.c
        igb.c
        ixgb.c
        ixgbe.c
        ixgbevf.c
        lan78xx.c
        marvell.c
        natsemi.c
        pcnet32.c
        qsfp.c
        realtek.c
        rxclass.c
        sfc.c
        sff-common.c
        sfpdiag.c
        sfpid.c
        smsc911x.c
        stmmac.c
        tg3.c
        tse.c
        vioc.c
        vmxnet3.c
        common.c
        cmis.c
        )
list(TRANSFORM ethtool_sources PREPEND "ethtool-5.18/")
add_executable(ethtool ${ethtool_sources})

#add_executable(ethtool
#        ethtool-5.18/amd8111e.c
#        ethtool-5.18/at76c50x-usb.c
#        ethtool-5.18/de2104x.c
#        ethtool-5.18/dsa.c
#        ethtool-5.18/e100.c
#        ethtool-5.18/e1000.c
#        ethtool-5.18/et131x.c
#        ethtool-5.18/ethtool.c
#        ethtool-5.18/fec.c
#        ethtool-5.18/fec_8xx.c
#        ethtool-5.18/fjes.c
#        ethtool-5.18/ibm_emac.c
#        ethtool-5.18/igb.c
#        ethtool-5.18/ixgb.c
#        ethtool-5.18/ixgbe.c
#        ethtool-5.18/ixgbevf.c
#        ethtool-5.18/lan78xx.c
#        ethtool-5.18/marvell.c
#        ethtool-5.18/natsemi.c
#        ethtool-5.18/pcnet32.c
#        ethtool-5.18/qsfp.c
#        ethtool-5.18/realtek.c
#        ethtool-5.18/rxclass.c
#        ethtool-5.18/sfc.c
#        ethtool-5.18/sff-common.c
#        ethtool-5.18/sfpdiag.c
#        ethtool-5.18/sfpid.c
#        ethtool-5.18/smsc911x.c
#        ethtool-5.18/stmmac.c
#        ethtool-5.18/tg3.c
#        ethtool-5.18/tse.c
#        ethtool-5.18/vioc.c
#        ethtool-5.18/vmxnet3.c
#        ethtool-5.18/common.c
#        ethtool-5.18/cmis.c
#        )
add_compile_definitions(PACKAGE="ethtool")
add_compile_definitions(VERSION="5.18")

#添加math库
target_link_libraries(ethtool m)