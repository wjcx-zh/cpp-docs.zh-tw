---
title: 批次模式規則 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b002b17fcc70ff4e374fb0630e9c18a52cbfc4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="batch-mode-rules"></a>批次模式規則
```  
{frompath}.fromext{topath}.toext::  
   commands  
```  
  
 當 N 命令通過此推斷規則時，批次模式推斷規則提供推斷規則只有一個引動的過程。 沒有批次模式推斷規則，將會要求 N 叫用的命令。 N 是推斷規則觸發程序的相依項目數目。  
  
 包含批次模式推斷規則的 Makefile 必須使用 NMAKE 1.62 或更高版本。 若要檢查 NMAKE 版本，請執行可用 _NMAKE_VER 巨集與 NMAKE 版本，1.62 或更高版本。 這個巨集會傳回字串，代表 Visual c + + 的產品版本。  
  
 之間唯一的語法差異的標準的推斷規則是以雙冒號 （:），終止批次模式推斷規則。  
  
> [!NOTE]
>  所叫用的工具必須能夠處理多個檔案。 必須使用批次模式推斷規則`$<`為巨集來存取相依的檔案。  
  
 批次模式推斷規則可以加快建置程序。 會比提供檔案給編譯器的批次，因為編譯器驅動程式會叫用一次。 例如，C 和 c + + 編譯器會執行更好時處理一組檔案，因為它可以保留記憶體常駐在程序期間。  
  
 下列範例會示範如何使用批次模式推斷規則：  
  
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
  
 NMAKE 會產生下列輸出沒有批次模式推斷規則：  
  
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
  
 NMAKE 會產生下列結果與批次模式推斷規則：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [推斷規則](../build/inference-rules.md)