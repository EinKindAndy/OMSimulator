project(OMSimulatorPython)

install(FILES OMSimulator.py DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)

IF (WIN32 AND MSVC)
  install(FILES OMSimulatorPython.bat DESTINATION ${CMAKE_INSTALL_PREFIX}/bin PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ)
ELSEIF (WIN32 AND MINGW)
  install(FILES OMSimulatorPython.bat DESTINATION ${CMAKE_INSTALL_PREFIX}/bin PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ)
  install(FILES OMSimulatorPython DESTINATION ${CMAKE_INSTALL_PREFIX}/bin PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ)
ELSEIF (APPLE)
  message(WARNING "OMSimulatorPython is not available on Mac OS X.")
ELSE ()
  install(FILES OMSimulatorPython DESTINATION ${CMAKE_INSTALL_PREFIX}/bin PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ)
ENDIF ()

IF (Ceres_FOUND AND OMSYSIDENT)
  install(FILES OMSysIdent.py DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
ENDIF ()
