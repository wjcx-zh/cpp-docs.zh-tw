---
title: "連結器工具警告 LNK4078 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4078
dev_langs: C++
helpviewer_keywords: LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8109ef98237f545a2139be8f0502acd11407314b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4078"></a>連結器工具警告 LNK4078
多個 '區段名稱' 區段有不同的屬性  
  
 連結兩個或多個具有相同的區段名稱但不同的屬性。  
  
 這個警告可能因舊版的連結或 LIB 所建立的匯入程式庫或匯出檔案。  
  
 重新建立檔案並重新連結。  
  
## <a name="example"></a>範例  
 LNK4078 也可能因重大變更： 所命名的區段[init_seg](../../preprocessor/init-seg.md) x86 上讀取/寫入，它現在為唯讀。  
  
 下列範例會產生 LNK4078。  
  
```  
// LNK4078.cpp  
// compile with: /W1  
// LNK4078 expected  
#include <stdio.h>  
#pragma warning(disable : 4075)  
typedef void (__cdecl *PF)(void);  
int cxpf = 0;   // number of destructors to call  
PF pfx[200];   // pointers to destructors.  
  
struct A { A() {} };  
  
int myexit (PF pf) { return 0; }  
  
#pragma section(".mine$a", read, write)  
// try the following line instead  
// #pragma section(".mine$a", read)  
__declspec(allocate(".mine$a")) int ii = 1;  
  
#pragma section(".mine$z", read, write)  
// try the following line instead  
// #pragma section(".mine$z", read)  
__declspec(allocate(".mine$z")) int i = 1;  
  
#pragma data_seg()  
#pragma init_seg(".mine$m", myexit)  
A bbbb;   
A cccc;  
int main() {}  
```