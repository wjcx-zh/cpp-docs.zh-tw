---
title: "編譯器錯誤 C2728 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2728
dev_langs:
- C++
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 4e28f463dffeda0bc1b44da4d4e228771f59cc4c
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2728"></a>編譯器錯誤 C2728
'type'：原生陣列不可包含這個類型  
  
 陣列建立語法是用來建立 Managed 或 WinRT 物件的陣列。 您不能使用原生陣列語法建立 Managed 或 WinRT 物件的陣列。  
  
 如需詳細資訊，請參閱[陣列](../../windows/arrays-cpp-component-extensions.md)。  
  
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

