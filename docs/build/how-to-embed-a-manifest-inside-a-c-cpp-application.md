---
title: "如何：在 C/C++ 應用程式中嵌入資訊清單 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內嵌的資訊清單"
  - "Makefile, 更新至內嵌資訊清單"
  - "資訊清單 [C++]"
ms.assetid: ec0bac69-2fdc-466c-ab0d-710a22974e5d
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：在 C/C++ 應用程式中嵌入資訊清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建議讓 C\/C\+\+ 應用程式 \(或程式庫\) 將其資訊清單嵌入最終二進位碼檔案，因為針對大部分案例，這麼做都能確保產生正確的執行階段行為。  當 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 從原始程式檔建置專案時，預設便會嵌入資訊清單。如需詳細資訊，請參閱[在 Visual Studio 中產生資訊清單](../build/manifest-generation-in-visual-studio.md)。  不過，如果是使用 nmake 建置應用程式，您就必須對現有的 Makefile 進行一些變更。  這一節將示範如何變更現有的 Makefile，以便能自動將資訊清單內嵌於最終二進位檔中。  
  
## 兩種作法  
 有兩種方式可以將資訊清單內嵌在應用程式或程式庫中。  
  
-   如果您不打算執行累加建置 \(Incremental Build\)，您可以使用類似下列命令列做為建置後步驟，以直接內嵌資訊清單：  
  
     **mt.exe –manifest MyApp.exe.manifest \-outputresource:MyApp.exe;1**  
  
     或  
  
     **mt.exe –manifest MyLibrary.dll.manifest \-outputresource:MyLibrary.dll;2**  
  
     \(1 用於 EXE，2 用於 DLL\)。  
  
-   如果您要執行累加建置 \(Incremental Build\)，則直接依上述方式編輯資源將會停用累加建置，導致完整重建，因此應該採取不同作法。  
  
    -   連結二進位檔，以產生 MyApp.exe.manifest 檔。  
  
    -   將資訊清單轉換為資源檔。  
  
    -   重新連結 \(累加\) 以將資訊清單資源內嵌至程式庫中。  
  
 下列範例示範如何變更 Makefile 以加入這兩種技巧。  
  
## Makefile \(之前\)  
 考慮 MyApp.exe \(從一個檔案建置出來的簡單應用程式\) 的 nmake 指令碼：  
  
```  
# build MyApp.exe  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
!endif  
  
MyApp.exe : MyApp.obj  
    link $** /out:$@ $(LFLAGS)  
  
MyApp.obj : MyApp.cpp  
  
clean :   
    del MyApp.obj MyApp.exe  
```  
  
 如果不變更此指令碼，並使用 Visual C\+\+ 執行，則會成功建立 MyApp.exe。  此指令碼也會建立外部資訊清單檔案 MyApp.exe.manifest，作業系統會在執行階段使用此檔案載入相依組件。  
  
 MyLibrary.dll 的 nmake 指令碼看起來非常類似：  
  
```  
# build MyLibrary.dll  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
LFLAGS=$(LFLAGS) /DLL  
  
!endif  
  
MyLibrary.dll : MyLibrary.obj  
    link $** /out:$@ $(LFLAGS)  
  
MyLibrary.obj : MyLibrary.cpp  
  
clean :   
    del MyLibrary.obj MyLibrary.dll  
```  
  
## Makefile \(之後\)  
 若要使用內嵌資訊清單進行建置，您必須對這些原始 Makefile 進行四項小變更。  對 MyApp.exe Makefile：  
  
```  
# build MyApp.exe  
!include makefile.inc  
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
!endif  
  
MyApp.exe : MyApp.obj  
    link $** /out:$@ $(LFLAGS)  
    $(_VC_MANIFEST_EMBED_EXE)  
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2  
  
MyApp.obj : MyApp.cpp  
  
clean :   
    del MyApp.obj MyApp.exe  
    $(_VC_MANIFEST_CLEAN)  
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3  
  
!include makefile.targ.inc  
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)  
```  
  
 對 MyLibrary.dll Makefile：  
  
```  
# build MyLibrary.dll  
!include makefile.inc  
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
LFLAGS=$(LFLAGS) /DLL  
  
!endif  
  
MyLibrary.dll : MyLibrary.obj  
    link $** /out:$@ $(LFLAGS)  
    $(_VC_MANIFEST_EMBED_DLL)  
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2.  
  
MyLibrary.obj : MyLibrary.cpp  
  
clean :   
    del MyLibrary.obj MyLibrary.dll  
    $(_VC_MANIFEST_CLEAN)  
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3.  
  
!include makefile.targ.inc  
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)  
```  
  
 實際的工作是由 Makefile 現在包含的兩個檔案 makefile.inc 和 makefile.targ.inc 來執行。  
  
 建立 makefile.inc，並將下列內容複製到檔案內：  
  
```  
# makefile.inc -- Include this file into existing makefile at the very top.  
  
# _VC_MANIFEST_INC specifies whether build is incremental (1 - incremental).  
# _VC_MANIFEST_BASENAME specifies name of a temporary resource file.  
  
!if "$(DEBUG)" == "1"  
CPPFLAGS=$(CPPFLAGS) /MDd  
LFLAGS=$(LFLAGS) /INCREMENTAL  
_VC_MANIFEST_INC=1  
_VC_MANIFEST_BASENAME=__VC90.Debug  
  
!else  
CPPFLAGS=$(CPPFLAGS) /MD  
_VC_MANIFEST_INC=0  
_VC_MANIFEST_BASENAME=__VC90  
  
!endif  
  
####################################################  
# Specifying name of temporary resource file used only in incremental builds:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
_VC_MANIFEST_AUTO_RES=$(_VC_MANIFEST_BASENAME).auto.res  
!else  
_VC_MANIFEST_AUTO_RES=  
!endif  
  
####################################################  
# _VC_MANIFEST_EMBED_EXE - command to embed manifest in EXE:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
  
#MT_SPECIAL_RETURN=1090650113  
#MT_SPECIAL_SWITCH=-notify_resource_update  
MT_SPECIAL_RETURN=0  
MT_SPECIAL_SWITCH=  
_VC_MANIFEST_EMBED_EXE= \  
if exist $@.manifest mt.exe -manifest $@.manifest -out:$(_VC_MANIFEST_BASENAME).auto.manifest $(MT_SPECIAL_SWITCH) & \  
if "%ERRORLEVEL%" == "$(MT_SPECIAL_RETURN)" \  
rc /r $(_VC_MANIFEST_BASENAME).auto.rc & \  
link $** /out:$@ $(LFLAGS)  
  
!else  
  
_VC_MANIFEST_EMBED_EXE= \  
if exist $@.manifest mt.exe -manifest $@.manifest -outputresource:$@;1  
  
!endif  
  
####################################################  
# _VC_MANIFEST_CLEAN - command to clean resources files generated temporarily:  
  
!if "$(_VC_MANIFEST_INC)" == "1"  
  
_VC_MANIFEST_CLEAN=-del $(_VC_MANIFEST_BASENAME).auto.res \  
    $(_VC_MANIFEST_BASENAME).auto.rc \  
    $(_VC_MANIFEST_BASENAME).auto.manifest  
  
!else  
  
_VC_MANIFEST_CLEAN=  
  
!endif  
  
# End of makefile.inc   
####################################################  
```  
  
 接著建立 makefile.targ.inc，並將下列內容複製到檔案內：  
  
```  
# makefile.targ.inc - include this at the very bottom of the existing makefile  
  
####################################################  
# Commands to generate initial empty manifest file and the RC file  
# that references it, and for generating the .res file:  
  
$(_VC_MANIFEST_BASENAME).auto.res : $(_VC_MANIFEST_BASENAME).auto.rc  
  
$(_VC_MANIFEST_BASENAME).auto.rc : $(_VC_MANIFEST_BASENAME).auto.manifest  
    type <<$@  
#include <winuser.h>  
1RT_MANIFEST"$(_VC_MANIFEST_BASENAME).auto.manifest"  
<< KEEP  
  
$(_VC_MANIFEST_BASENAME).auto.manifest :  
    type <<$@  
<?xml version='1.0' encoding='UTF-8' standalone='yes'?>  
<assembly xmlns='urn:schemas-microsoft-com:asm.v1' manifestVersion='1.0'>  
</assembly>  
<< KEEP  
  
# end of makefile.targ.inc  
```  
  
## 請參閱  
 [了解 C\/C\+\+ 程式的資訊清單產生過程](../build/understanding-manifest-generation-for-c-cpp-programs.md)