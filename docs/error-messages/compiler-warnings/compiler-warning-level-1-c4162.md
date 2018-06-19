---
title: 編譯器警告 （層級 1） C4162 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4162
dev_langs:
- C++
helpviewer_keywords:
- C4162
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2789f6aa63c8a547a34ec6adfd89c1e1163c68e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287523"
---
# <a name="compiler-warning-level-1-c4162"></a>編譯器警告 （層級 1） c4162:
'identifier': 使用 C 連結，找到的函式  
  
 具有 C 連結的函式宣告，但找不到。  
  
 若要解決這個警告，編譯.c 檔案中 （叫用 C 編譯器）。  如果您必須叫用 c + + 編譯器，將 extern"C"函式宣告之前。  
  
 下列範例會產生 c4162:  
  
```  
// C4162.cpp  
// compile with: /c /W1  
unsigned char _bittest(long* a, long b);  
#pragma intrinsic (_bittest)   // C4162  
  
int main() {  
   bool bit;  
   long num = 78002;  
   bit = _bittest(&num, 5);  
}  
```  
  
 可能的解決方式：  
  
```  
// C4162b.cpp  
// compile with: /c  
extern "C"  
unsigned char _bittest(long* a, long b);  
#pragma intrinsic (_bittest)  
  
int main() {  
   bool bit;  
   long num = 78002;  
   bit = _bittest(&num, 5);  
}  
```