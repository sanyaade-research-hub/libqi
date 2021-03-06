## Copyright (c) 2012 Aldebaran Robotics. All rights reserved.
## Use of this source code is governed by a BSD-style license that can be
## found in the COPYING file.
qi_create_bin(testlaunch NO_INSTALL testlaunch.cpp)
qi_create_bin(testlaunchloop NO_INSTALL testlaunchloop.cpp)
qi_create_bin(check_env  NO_INSTALL check_env.cpp)

qi_use_lib(testlaunchloop QI)
qi_use_lib(check_env QI)

set_target_properties(testlaunch PROPERTIES FOLDER tests)
set_target_properties(testlaunchloop PROPERTIES FOLDER tests)
set_target_properties(check_env  PROPERTIES FOLDER tests)

qi_create_gtest(test_qipath      SRC test_qipath.cpp ../src/utils.cpp DEPENDS QI GTEST)
qi_create_gtest(test_qipath_from_bin SRC test_qipath.cpp ../src/utils.cpp DEPENDS QI GTEST)
if(BUILD_TESTS)
  set_tests_properties(test_qipath_from_bin PROPERTIES
      WORKING_DIRERCTORY ${QI_SDK_DIR}/${QI_SDK_BIN})
endif()
qi_create_gtest(test_qilocal     SRC test_locale.cpp      DEPENDS QI GTEST)
qi_create_gtest(test_qios        SRC test_qios.cpp        DEPENDS QI GTEST)
qi_create_gtest(test_thread      SRC test_thread.cpp      DEPENDS QI BOOST_THREAD)
qi_create_gtest(test_qilaunch    SRC test_qilaunch.cpp    DEPENDS QI GTEST)
qi_create_gtest(test_qilog_sync  SRC test_qilog_sync.cpp  DEPENDS QI GTEST)
qi_create_gtest(test_qilog_async SRC test_qilog_async.cpp DEPENDS QI GTEST)
