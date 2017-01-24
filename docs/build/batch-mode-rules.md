---
title: "批次模式規則 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "NMAKE 中的批次模式推斷規則"
  - "NMAKE 中的推斷規則"
  - "NMAKE 程式, 推斷規則"
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 批次模式規則
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

```  
{frompath}.fromext{topath}.toext::  
   commands  
```  
  
 當 N 命令通過這個推斷規則時，批次模式推斷規則只提供一個推斷規則的引動過程。  沒有批次模式推斷規則的話，叫用時會需要 N 命令。  N 是觸發推斷規則的相依性數目。  
  
 包含批次模式推斷規則的 Makefile 必須使用 NMAKE 1.62 版或更新的版本。  若要檢查 NMAKE 版本，請執行 NMAKE 1.62 版或更新版本所提供的 \_NMAKE\_VER 巨集。  這個巨集會傳回表示 Visual C\+\+ 產品版本的字串。  
  
 與標準的推斷規則之間唯一的語法差異在於，批次模式推斷規則是以雙冒號 \(::\) 結束。  
  
> [!NOTE]
>  叫用的工具必須要能處理多個檔案。  批次模式推斷規則必須將 `$<` 當做巨集使用，以便存取相依檔案。  
  
 批次模式推斷規則可以加速建置程序。  提供檔案給批次中的編譯器比較快速，因為只會叫用編譯器驅動程式一次。  例如，C 和 C\+\+ 編譯器在處理一組檔案時會執行得更好，因為編譯器可以在過程中保留記憶體常駐。  
  
 下列範例示範如何使用批次模式推斷規則：  
  
```  
#  
# sample makefile to illustrate batch-mode inference rules  
#  
O = .  
S = .  
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj  
CFLAGS = -nologo  
  
all : $(Objs)  
  
!ifdef NOBatch  
{$S}.cpp{$O}.obj:  
!else  
{$S}.cpp{$O}.obj::  
!endif  
   $(CC) $(CFLAGS) -Fd$O\ -c $<  
  
$(Objs) :  
  
#end of makefile  
```  
  
 NMAKE 產生下列沒有批次模式推斷規則的輸出：  
  
```  
E:\tmp> nmake -f test.mak -a NOBatch=1  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
        cl -nologo -Fd.\ -c .\foo1.cpp  
foo1.cpp  
        cl -nologo -Fd.\ -c .\foo2.cpp  
foo2.cpp  
        cl -nologo -Fd.\ -c .\foo3.cpp  
foo3.cpp  
        cl -nologo -Fd.\ -c .\foo4.cpp  
foo4.cpp  
```  
  
 NMAKE 產生下列具有批次模式推斷規則的結果：  
  
```  
E:\tmp> nmake -f test.mak -a  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
  
        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp  
foo1.cpp  
foo2.cpp  
foo3.cpp  
foo4.cpp  
Generating Code...  
```  
  
## 請參閱  
 [推斷規則](../build/inference-rules.md)