---
title: "編譯器錯誤 C3320 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3320
dev_langs:
- C++
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
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
translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 4b4acfe97e38cf13e336b7c58ffc868c69cf7a09
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3320"></a>編譯器錯誤 C3320
'type': 類型不可擁有與模組 'name' 屬性相同的名稱  
  
匯出的使用者定義的型別 (UDT)，這可能是結構、 類別、 列舉或等位，不能有相同的名稱作為參數傳遞至[模組](../../windows/module-cpp.md)屬性的名稱屬性。  
  
## <a name="example"></a>範例  
下列範例會產生 C3320：  
  
```cpp  
// C3320.cpp  
#include "unknwn.h"  
[module(name="xx")];  
  
[export] struct xx {   // C3320  
// Try the following line instead  
// [export] struct yy {  
   int i;  
};  
```
