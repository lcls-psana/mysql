#--------------------------------------------------------------------------
# File and Version Information:
#  $Id: SConscript 184 2009-01-31 08:22:52Z salnikov $
#
# Description:
#  SConscript file for package unixodbc
#------------------------------------------------------------------------

# Do not delete following line, it must be present in 
# SConscript file for any SIT project
Import('*')

import os
import subprocess
from os.path import join as pjoin

from SConsTools.CondaMeta import condaPackageExists
from SConsTools.standardCondaPackage import standardCondaPackage

REQUIRED_PKGLIBS='mysqlclient'
standardCondaPackage('mysql', **locals())

#
# very special target which makes libmysql_soname.h header 
#
def make_libmysql_soname_header(env, target, source):
    trgt = open(str(target[0]), "w")
    trgt.write('const char* const libmysql_soname = "libmysqlclient.so";')
    trgt.close()
    
header = "#arch/$SIT_ARCH/geninc/mysql/libmysql_soname.h"
target = env.Command(header, None, make_libmysql_soname_header)
env['ALL_TARGETS']['INCLUDES'].append(target)
