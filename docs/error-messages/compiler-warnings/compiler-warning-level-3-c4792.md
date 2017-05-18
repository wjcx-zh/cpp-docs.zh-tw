---
title: "編譯器警告 （層級 3） C4792 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4792
dev_langs:
- C++
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 7886d2b28c9120e2e764dedd0ecc72265fe91be5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4792"></a>編譯器警告 (層級 3) C4792
使用 sysimport 宣告並從機器碼參考的函式 'function'; 匯入程式庫需要連結  
  
 已從 Unmanaged 函式呼叫使用 DllImport 匯入至程式的原生函式。 因此，您必須連結至 DLL 的匯入程式庫。  
  
 透過程式碼，或變更編譯方式，並無法解決這個警告。 使用[警告](../../preprocessor/warning.md)pragma 來停用這個警告。  
  
 下列範例會產生 C4792：  
  
```  
// C4792.cpp  
// compile with: /clr /W3  
// C4792 expected  
using namespace System::Runtime::InteropServices;  
[DllImport("msvcrt")]  
extern "C" int __cdecl puts(const char *);  
int main() {}  
  
// Uncomment the following line to resolve.  
// #pragma warning(disable : 4792)  
#pragma unmanaged  
void func(void){  
   puts("test");  
}  
```
