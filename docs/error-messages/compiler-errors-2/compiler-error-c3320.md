---
title: "編譯器錯誤 C3320 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3320
dev_langs:
- C++
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c729bf63fae7a7181496e1901dda1d8ac5bdfa50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3320"></a>編譯器錯誤 C3320
'type': 類型不可擁有與模組 'name' 屬性相同的名稱  
  
匯出的使用者定義的型別 (UDT)，這可能是結構、 類別、 列舉或等位，不能有相同的名稱，為參數傳遞至[模組](../../windows/module-cpp.md)屬性的名稱屬性。  
  
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