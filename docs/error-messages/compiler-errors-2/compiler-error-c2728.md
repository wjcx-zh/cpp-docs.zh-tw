---
title: 編譯器錯誤 C2728 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2728
dev_langs:
- C++
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e954ba38efc2e1ef7bc4b203c8b54876f7aae0ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2728"></a>編譯器錯誤 C2728
'type'：原生陣列不可包含這個類型  
  
 陣列建立語法是用來建立 Managed 或 WinRT 物件的陣列。 您不能使用原生陣列語法建立 Managed 或 WinRT 物件的陣列。  
  
 如需詳細資訊，請參閱 [陣列](../../windows/arrays-cpp-component-extensions.md)。  
  
 下列範例會產生 C2728，並示範如何修正此問題：  
  
```  
// C2728.cpp  
// compile with: /clr  
  
int main() {  
   int^ arr[5];   // C2728  
  
   // try the following line instead  
   array<int>^arr2;  
}  
```  
