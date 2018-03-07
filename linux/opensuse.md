### opensuse跨版本升级
    #方法1
    sudo sed -i "s/42.2/42.3/g" /etc/zypp/repos.d/*

    #方法2
    sudo zypper mr -da
    sudo zypper ar -f http://mirrors.ustc.edu.cn/opensuse/distribution/leap/42.3/repo/oss/ USTC-OSS
    sudo zypper ar -f http://mirrors.ustc.edu.cn/opensuse/distribution/leap/42.3/repo/non-oss/ USTC-NON-OSS
    sudo zypper ar -f http://mirrors.ustc.edu.cn/opensuse/update/leap/42.3/non-oss/ USTC-UP-O
    sudo zypper ar -f http://mirrors.ustc.edu.cn/opensuse/update/leap/42.3/oss/ USTC-UP-N
    sudo zypper ar -f http://packman.inode.at/suse/openSUSE_Leap_42.3/ packman

    #然后做
    sudo zypper ref
    
    sudo zypper dup -y --auto-agree-with-licenses