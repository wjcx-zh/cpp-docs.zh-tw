---
title: "編譯器錯誤 C3901 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3901
dev_langs: C++
helpviewer_keywords: C3901
ms.assetid: 19af4141-39ad-4c16-a68f-3ae76f648186
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 778bb3336d33c52ce0efcefe96d4da304c1502cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3901"></a>編譯器錯誤 C3901
'accessor_function': 必須有傳回類型 'type'  
  
 至少一個 get 方法的傳回類型必須符合屬性類型。 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md)。  
  
 下列範例會產生 C3901:  
  
```  
// C3901.cpp  
// compile with: /clr /c  
using namespace System;  
ref class X {  
   property String^ Name {  
      void get();   // C3901  
      // try the following line instead  
      // String^ get();  
   };  
};  
  
ref class Y {  
   property double values[int, int] {  
      int get(int, int);   // C3901  
      // try the following line instead  
      // double get(int, int);  
   };  
};  
```