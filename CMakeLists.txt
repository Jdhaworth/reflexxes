cmake_minimum_required(VERSION 3.8)
project(reflexxes)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)

include_directories( include )

add_library( ReflexxesTypeII SHARED

src/TypeIIRML/ReflexxesAPI.cpp                             
src/TypeIIRML/TypeIIRMLStep1IntermediateProfiles.cpp
src/TypeIIRML/TypeIIRMLCalculatePositionalExtrems.cpp      
src/TypeIIRML/TypeIIRMLStep1Profiles.cpp
src/TypeIIRML/TypeIIRMLDecisions.cpp                       
src/TypeIIRML/TypeIIRMLStep2.cpp
src/TypeIIRML/TypeIIRMLDecisionTree1A.cpp                  
src/TypeIIRML/TypeIIRMLStep2IntermediateProfiles.cpp
src/TypeIIRML/TypeIIRMLDecisionTree1B.cpp                  
src/TypeIIRML/TypeIIRMLStep2PhaseSynchronization.cpp
src/TypeIIRML/TypeIIRMLDecisionTree1C.cpp                  
src/TypeIIRML/TypeIIRMLStep2Profiles.cpp
src/TypeIIRML/TypeIIRMLDecisionTree2.cpp                   
src/TypeIIRML/TypeIIRMLStep2WithoutSynchronization.cpp
src/TypeIIRML/TypeIIRMLFallBackStrategy.cpp                
src/TypeIIRML/TypeIIRMLStep3.cpp
src/TypeIIRML/TypeIIRMLIsPhaseSynchronizationPossible.cpp  
src/TypeIIRML/TypeIIRMLVelocityCalculatePositionalExtrems.cpp
src/TypeIIRML/TypeIIRMLPolynomial.cpp                      
src/TypeIIRML/TypeIIRMLVelocity.cpp
src/TypeIIRML/TypeIIRMLPosition.cpp                        
src/TypeIIRML/TypeIIRMLVelocityFallBackStrategy.cpp
src/TypeIIRML/TypeIIRMLQuicksort.cpp                       
src/TypeIIRML/TypeIIRMLVelocityIsPhaseSynchronizationPossible.cpp
src/TypeIIRML/TypeIIRMLSetupModifiedSelectionVector.cpp    
src/TypeIIRML/TypeIIRMLVelocityMethods.cpp
src/TypeIIRML/TypeIIRMLStep1.cpp                           
src/TypeIIRML/TypeIIRMLVelocitySetupPhaseSyncSelectionVector.cpp

)

install( TARGETS ReflexxesTypeII LIBRARY DESTINATION lib )

install( DIRECTORY include/ DESTINATION include )

# Export via these functions rather than ament_export_targets since we aren't doing a target based install
ament_export_include_directories(include)
ament_export_libraries(ReflexxesTypeII)

ament_package()