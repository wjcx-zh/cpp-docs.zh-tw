---
title: "連結器工具警告 LNK4217 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4217
dev_langs: C++
helpviewer_keywords: LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 09c984d7675c73bdf225bae7d3014f81153d20e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4217"></a>連結器工具警告 LNK4217
本機定義的符號 'symbol' 函式 'function' 中匯入  
  
 [__declspec （dllimport)](../../cpp/dllexport-dllimport.md)符號指定即使在本機定義的符號。 移除`__declspec`修飾詞，以解決這個警告。  
  
 `symbol`是映像內已定義的符號名稱。 `function`為正在匯入符號函式。  
  
 當您使用選項編譯時，不會出現這個警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 如果您嘗試連結這兩個模組，相反地，您應該編譯第二個模組的第一個模組匯入程式庫時，也會發生 LNK4217。  
  
```  
// LNK4217.cpp  
// compile with: /LD  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 然後，  
  
```  
// LNK4217b.cpp  
// compile with: /c  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 嘗試連結這兩個模組，將會導致 LNK4217，編譯第二個範例的第一個範例若要解決匯入程式庫。