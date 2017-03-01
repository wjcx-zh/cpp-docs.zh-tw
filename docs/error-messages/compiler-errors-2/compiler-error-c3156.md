---
title: "編譯器錯誤 C3156 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3156
dev_langs:
- C++
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 170a76ba617396d716243e215d13c264f48cf5bf
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3156"></a>編譯器錯誤 C3156
'class'：您無法具有一個 managed 或 WinRT 類型的本機定義  
  
 函式不可包含 managed 或 WinRT 類別、結構或介面的定義或宣告。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3156。  
  
```  
// C3156.cpp  
// compile with: /clr /c  
void f() {  
   ref class X {};   // C3156  
   ref class Y;   // C3156  
}  
```  

