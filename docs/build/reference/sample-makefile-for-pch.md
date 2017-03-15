---
title: "PCH 的 Makefile 範例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
ms.assetid: daf68983-77dc-45db-8701-aa89ad18910d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# PCH 的 Makefile 範例
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列 Makefile 使用巨集和 \!IF、\!ELSE、\!ENDIF 流程控制命令結構來簡化與您專案的配合。  
  
```  
# Makefile : Illustrates the effective use of precompiled  
#            headers in a project  
# Usage:     NMAKE option  
# option:    DEBUG=[0|1]  
#            (DEBUG not defined is equivalent to DEBUG=0)  
#  
OBJS = myapp.obj applib.obj  
# List all stable header files in the STABLEHDRS macro.  
STABLEHDRS = stable.h another.h  
# List the final header file to be precompiled here:  
BOUNDRY = stable.h  
# List header files under development here:  
UNSTABLEHDRS = unstable.h  
# List all compiler options common to both debug and final  
# versions of your code here:  
CLFLAGS = /c /W3  
# List all linker options common to both debug and final  
# versions of your code here:  
LINKFLAGS = /NOD /ONERROR:NOEXE  
!IF "$(DEBUG)" == "1"  
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi /f  
LINKFLAGS = $(LINKFLAGS) /COD  
LIBS      = slibce  
!ELSE  
CLFLAGS   = $(CLFLAGS) /Oselg /Gs  
LINKFLAGS = $(LINKFLAGS)  
LIBS      = slibce  
!ENDIF  
myapp.exe: $(OBJS)  
    link $(LINKFLAGS) @<<  
$(OBJS), myapp, NUL, $(LIBS), NUL;  
<<  
# Compile myapp  
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch  
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp  
# Compile applib  
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch  
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp  
# Compile headers  
stable.pch : $(STABLEHDRS)  
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp  
```  
  
 除了[建置程序中的 PCH 檔](../../build/reference/pch-files-in-the-build-process.md)中的「使用先行編譯標頭檔之 Makefile 的結構」圖中顯示的 STABLEHDRS、BOUNDRY 和 UNSTABLEHDRS 巨集以外，這個 Makefile 提供 CLFLAGS 巨集和 LINKFLAGS 巨集。  無論您建置的應用程式可執行檔是偵錯版還是最終版，都必須使用這些巨集來列出要套用的編譯器及連結器選項。  還有一個是您在該處列出專案所需程式庫的 LIBS 巨集。  
  
 Makefile 並使用 \!IF、\!ELSE、\!ENDIF 來偵測您是否在 NMAKE 命令列上定義 DEBUG 符號：  
  
```  
NMAKE DEBUG=[1|0]  
```  
  
 這項功能讓您可在開發期間及程式的最終版本時使用相同的 Makefile \(對最終版本請使用 DEBUG\=0\)。  下列命令列是相等：  
  
```  
NMAKE   
NMAKE DEBUG=0  
```  
  
 如需 Makefile 的詳細資訊，請參閱 [NMAKE 參考](../../build/nmake-reference.md)。  請參閱[編譯器選項](../../build/reference/compiler-options.md)和[連結器選項](../../build/reference/linker-options.md)。  
  
## 請參閱  
 [在專案中使用先行編譯的標頭](../../build/reference/using-precompiled-headers-in-a-project.md)