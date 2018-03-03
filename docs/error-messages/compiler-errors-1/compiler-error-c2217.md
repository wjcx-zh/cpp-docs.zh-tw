---
title: "編譯器錯誤 C2217 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2217
dev_langs:
- C++
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6af2bbd43d6e522bbe6ede2a874b7e8ebbf27c10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2217"></a>編譯器錯誤 C2217
'attribute1' 需要 'attribute2'  
  
 第一個函式屬性需要第二個屬性。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  插斷 (`__interrupt`) 函式宣告為`near`。 插斷函式必須是`far`。  
  
2.  中斷與宣告的函式`__stdcall`，或`__fastcall`。 插斷函式必須使用 C 呼叫慣例。  
  
## <a name="example"></a>範例  
 如果您嘗試將委派繫結的 CLR 函式接受可變數目的引數，也會發生 C2217。 如果函式也有 e param 陣列的多載，改用該複本。 下列範例會產生 C2217。  
  
```  
// C2217.cpp  
// compile with: /clr  
using namespace System;  
delegate void MyDel(String^, Object^, Object^, ...);   // C2217  
delegate void MyDel2(String ^, array<Object ^> ^);   // OK  
  
int main() {  
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);  
   array<Object ^ > ^ x = gcnew array<Object ^>(2);  
   x[0] = safe_cast<Object^>(0);  
   x[1] = safe_cast<Object^>(1);  
  
   // wl("{0}, {1}", 0, 1);  
   wl("{0}, {1}", x);  
}  
```