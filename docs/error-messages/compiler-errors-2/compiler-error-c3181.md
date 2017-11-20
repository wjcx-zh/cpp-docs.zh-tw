---
title: "編譯器錯誤 C3181 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3181
dev_langs: C++
helpviewer_keywords: C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 84f725f64e22dc5da1736eb64696b03b0b7ea36a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3181"></a>編譯器錯誤 C3181
'type': 運算子的運算元無效  
  
無效的參數傳遞給[typeid](../../windows/typeid-cpp-component-extensions.md)運算子。 參數必須是 managed 型別。  
  
請注意，編譯器會使用別名，對應至 common language runtime 中類型的原生類型。  
  
下列範例會產生 C3181:  
  
```  
// C3181a.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181  
   Type ^pType2 = int::typeid;   // OK  
}  
```  
