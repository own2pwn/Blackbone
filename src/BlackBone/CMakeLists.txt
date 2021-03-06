cmake_minimum_required (VERSION 2.8)
project (BlackBone)

include_directories(../../Contrib)

add_definitions(-DBLACKBONE_STATIC)

##########################################################
set(SOURCE_ASMJIT   ../../contrib/asmjit/base/assembler.cpp
                    ../../contrib/Asmjit/base/codegen.cpp
                    ../../contrib/Asmjit/base/constpool.cpp
                    ../../contrib/Asmjit/base/containers.cpp
                    ../../contrib/Asmjit/base/cpuinfo.cpp
                    ../../contrib/Asmjit/base/cputicks.cpp
                    ../../contrib/Asmjit/base/error.cpp
                    ../../contrib/Asmjit/base/globals.cpp
                    ../../contrib/Asmjit/base/operand.cpp
                    ../../contrib/Asmjit/base/runtime.cpp
                    ../../contrib/Asmjit/base/string.cpp
                    ../../contrib/Asmjit/base/vmem.cpp
                    ../../contrib/Asmjit/base/zone.cpp
                    ../../contrib/Asmjit/x86/x86assembler.cpp
                    ../../contrib/Asmjit/x86/x86cpuinfo.cpp
                    ../../contrib/Asmjit/x86/x86inst.cpp
                    ../../contrib/Asmjit/x86/x86operand.cpp
                    ../../contrib/Asmjit/x86/x86operand_regs.cpp)
                    
set (HEADER_ASMJIT  ../../contrib/Asmjit/apibegin.h
                    ../../contrib/Asmjit/apiend.h
                    ../../contrib/Asmjit/asmjit.h
                    ../../contrib/Asmjit/base.h
                    ../../contrib/Asmjit/build.h
                    ../../contrib/Asmjit/config.h
                    ../../contrib/Asmjit/host.h
                    ../../contrib/Asmjit/x86.h
                    ../../contrib/Asmjit/base/assembler.h
                    ../../contrib/Asmjit/base/codegen.h
                    ../../contrib/Asmjit/base/compiler.h
                    ../../contrib/Asmjit/base/constpool.h
                    ../../contrib/Asmjit/base/containers.h
                    ../../contrib/Asmjit/base/context_p.h
                    ../../contrib/Asmjit/base/cpuinfo.h
                    ../../contrib/Asmjit/base/cputicks.h
                    ../../contrib/Asmjit/base/error.h
                    ../../contrib/Asmjit/base/globals.h
                    ../../contrib/Asmjit/base/intutil.h
                    ../../contrib/Asmjit/base/lock.h
                    ../../contrib/Asmjit/base/logger.h
                    ../../contrib/Asmjit/base/operand.h
                    ../../contrib/Asmjit/base/runtime.h
                    ../../contrib/Asmjit/base/string.h
                    ../../contrib/Asmjit/base/vectypes.h
                    ../../contrib/Asmjit/base/vmem.h
                    ../../contrib/Asmjit/base/zone.h
                    ../../contrib/Asmjit/x86/x86assembler.h
                    ../../contrib/Asmjit/x86/x86compiler.h
                    ../../contrib/Asmjit/x86/x86context_p.h
                    ../../contrib/Asmjit/x86/x86cpuinfo.h
                    ../../contrib/Asmjit/x86/x86inst.h
                    ../../contrib/Asmjit/x86/x86operand.h
                    ../../contrib/Asmjit/x86/x86scheduler_p.h)
                    
FILE(GLOB AsmJit ${SOURCE_ASMJIT} ${HEADER_ASMJIT})
source_group(AsmJit\\Core FILES ${AsmJit})

##########################################################
set(SOURCE_HELPERS  Asm/AsmHelper32.cpp
                    Asm/AsmHelper64.cpp
                    Asm/LDasm.c)
                    
set(HEADER_HELPERS  Asm/AsmHelper.h
                    Asm/AsmHelper32.h
                    Asm/AsmHelper64.h
                    Asm/AsmHelperBase.h
                    Asm/AsmStack.hpp
                    Asm/AsmVariant.hpp
                    Asm/LDasm.h)
                    
FILE(GLOB AsmJitHelpers ${SOURCE_HELPERS} ${HEADER_HELPERS})
source_group(AsmJit\\Helpers FILES ${AsmJitHelpers})

##########################################################
set(SOURCE_DRV      DriverControl/DriverControl.cpp)                  
set(HEADER_DRV      DriverControl/DriverControl.h)
                    
FILE(GLOB DriverControl ${SOURCE_DRV} ${HEADER_DRV})
source_group(DriverControl FILES ${DriverControl})

##########################################################                    
set(HEADER_INCLUDE  Include/FunctionTypes.h
                    Include/Macro.h
                    Include/NativeStructures.h
                    Include/Types.h
                    Include/Win7Specific.h
                    Include/Win8Specific.h
                    Include/Winheaders.h
                    Include/WinXPSpecific.h)
                    
FILE(GLOB Include ${HEADER_INCLUDE})
source_group(Include FILES ${Include})

##########################################################
set(SOURCE_LOCALHK  LocalHook/LocalHookBase.cpp
                    LocalHook/TraceHook.cpp)
                    
set(HEADER_LOCALHK  LocalHook/HookHandlerCdecl.h
                    LocalHook/HookHandlerFastcall.h
                    LocalHook/HookHandlers.h
                    LocalHook/HookHandlerStdcall.h
                    LocalHook/HookHandlerThiscall.h
                    LocalHook/LocalHook.hpp
                    LocalHook/LocalHookBase.h
                    LocalHook/TraceHook.h
                    LocalHook/VTableHook.hpp)
                    
FILE(GLOB LocalHook ${SOURCE_LOCALHK} ${HEADER_LOCALHK})
source_group(LocalHook FILES ${LocalHook})

##########################################################
set(SOURCE_MMAP     ManualMap/MExcept.cpp
                    ManualMap/MMap.cpp
                    ManualMap/Native/NtLoader.cpp)
                    
set(HEADER_MMAP     ManualMap/MExcept.h
                    ManualMap/MMap.h
                    ManualMap/Native/NtLoader.h)
                    
FILE(GLOB ManualMap ${SOURCE_MMAP} ${HEADER_MMAP})
source_group(ManualMap FILES ${ManualMap})

##########################################################
set(SOURCE_MISC     Misc/DynImport.cpp
                    Misc/NameResolve.cpp
                    Misc/Utils.cpp)
                    
set(HEADER_MISC     Misc/DynImport.h
                    Misc/NameResolve.h
                    Misc/Thunk.hpp
                    Misc/Trace.hpp
                    Misc/Utils.h)
                    
FILE(GLOB Misc ${SOURCE_MISC} ${HEADER_MISC})
source_group(Misc FILES ${Misc})

##########################################################
set(SOURCE_PATTERN  Patterns/PatternSearch.cpp)                  
set(HEADER_PATTERN  Patterns/PatternSearch.h)
                    
FILE(GLOB Patterns ${SOURCE_PATTERN} ${HEADER_PATTERN})
source_group(Patterns FILES ${Patterns})

##########################################################
set(SOURCE_PE       PE/ImageNET.cpp PE/PEImage.cpp)                  
set(HEADER_PE       PE/ImageNET.h   PE/PEImage.h)
                    
FILE(GLOB PE ${SOURCE_PE} ${HEADER_PE})
source_group(PE FILES ${PE})

##########################################################
set(SOURCE_PROCESS  Process/MemBlock.cpp
                    Process/Process.cpp
                    Process/ProcessCore.cpp
                    Process/ProcessMemory.cpp
                    Process/ProcessModules.cpp)
                    
set(HEADER_PROCESS  Process/MemBlock.h
                    Process/Process.h
                    Process/ProcessCore.h
                    Process/ProcessMemory.h
                    Process/ProcessModules.h)
                    
FILE(GLOB Process ${SOURCE_PROCESS} ${HEADER_PROCESS})
source_group(Process FILES ${Process})

##########################################################
set(SOURCE_RPC      Process/RPC/RemoteExec.cpp
                    Process/RPC/RemoteHook.cpp
                    Process/RPC/RemoteLocalHook.cpp
                    Process/RPC/RemoteMemory.cpp)
                    
set(HEADER_RPC      Process/RPC/RemoteContext.hpp
                    Process/RPC/RemoteExec.h
                    Process/RPC/RemoteFunction.hpp
                    Process/RPC/RemoteHook.h
                    Process/RPC/RemoteLocalHook.h
                    Process/RPC/RemoteMemory.h)
                    
FILE(GLOB RPC ${SOURCE_RPC} ${HEADER_RPC})
source_group(Process\\Remote FILES ${RPC})

##########################################################
set(SOURCE_THREADS  Process/Threads/Thread.cpp Process/Threads/Threads.cpp)                 
set(HEADER_THREADS  Process/Threads/Thread.h   Process/Threads/Threads.h)
                    
FILE(GLOB Threads ${SOURCE_THREADS} ${HEADER_THREADS})
source_group(Process\\Threads FILES ${Threads})

##########################################################
set(SOURCE_SUB      Subsystem/NativeSubsystem.cpp
                    Subsystem/Wow64Local.cpp
                    Subsystem/Wow64Subsystem.cpp
                    Subsystem/x86Subsystem.cpp)
                    
set(HEADER_SUB      Subsystem/NativeSubsystem.h
                    Subsystem/Wow64Local.h
                    Subsystem/Wow64Subsystem.h
                    Subsystem/x86Subsystem.h)
                    
FILE(GLOB Subsystem ${SOURCE_SUB} ${HEADER_SUB})
source_group(Subsystem FILES ${Subsystem})
                
##########################################################
set (HEADER_MAIN    Config.h )

##########################################################                
set(SOURCE_LIB      ${SOURCE_ASMJIT} 
                    ${SOURCE_HELPERS} 
                    ${SOURCE_DRV}
                    ${SOURCE_LOCALHK}
                    ${SOURCE_MMAP}
                    ${SOURCE_MISC}
                    ${SOURCE_PATTERN}
                    ${SOURCE_PE}
                    ${SOURCE_PROCESS}
                    ${SOURCE_RPC}
                    ${SOURCE_THREADS}
                    ${SOURCE_SUB}) 
                    
set(HEADER_LIB      ${HEADER_ASMJIT} 
                    ${HEADER_HELPERS} 
                    ${HEADER_DRV}
                    ${HEADER_INCLUDE}
                    ${HEADER_LOCALHK}
                    ${HEADER_MMAP}
                    ${HEADER_MISC}
                    ${HEADER_PATTERN}
                    ${HEADER_PE}
                    ${HEADER_PROCESS}
                    ${HEADER_RPC}
                    ${HEADER_THREADS}
                    ${HEADER_SUB}
                    ${HEADER_MAIN})

add_library(BlackBone STATIC ${SOURCE_LIB} ${HEADER_LIB})