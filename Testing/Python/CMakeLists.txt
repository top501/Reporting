
#
# Install test data
#
message("Module source dir is ${MODULE_SOURCE_DIR}")
set(TEST_DATA_DIR ${MODULE_SOURCE_DIR}/Prototype/TestData/DICOM.CT)
set(TEMP "${CMAKE_BINARY_DIR}/Testing/Temporary/DICOM.CT")
MESSAGE(STATUS "Reporting: copying files from ${TEST_DATA_DIR} to ${TEMP}")
configure_file(
  ${TEST_DATA_DIR}/instance_487.dcm
  ${TEMP}/instance_487.dcm
  COPYONLY)
configure_file(
  ${TEST_DATA_DIR}/instance_488.dcm
  ${TEMP}/instance_488.dcm
  COPYONLY)
configure_file(
  ${TEST_DATA_DIR}/instance_489.dcm
  ${TEMP}/instance_489.dcm
  COPYONLY)

slicer_add_python_unittest(
  SCRIPT ReportingRoundTripTest.py
  SLICER_ARGS --disable-cli-modules
              --additional-module-paths "${CMAKE_BINARY_DIR}/${Slicer_QTLOADABLEMODULES_LIB_DIR} ${Slicer_DIR}/${Slicer_QTSCRIPTEDMODULES_LIB_DIR}"
  )
