---
title: "編譯器錯誤 C3861 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3861"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3861"
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3861
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier'：找不到識別項  
  
 即使使用引數相依查閱，編譯器仍無法解析識別項的參考。  
  
 若要修正此錯誤，請檢查識別項宣告的大小寫和拼字。  確認已正確使用[範圍解析運算子](../../cpp/scope-resolution-operator.md)和命名空間 [using 指示詞](../../misc/using-directive-cpp.md)。  如果標頭檔中已宣告識別項，請確認在參考標頭之前，是否已將其包含在內。  也請檢查[條件式編譯指示詞](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)未排除的識別項。  
  
## 範例  
 下列範例會產生 C3861。  
  
```  
// C3861.cpp  
void f2(){}  
int main() {  
   f();   // C3861  
   f2();   // OK  
}  
```  
  
## 範例  
 C\+\+ 標準程式庫中的 Exception 類別現在會出現在 `std` 命名空間中。  
  
```  
// C3861_b.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   try {  
      throw exception("Exception");   // C3861  
      // try the following line instead  
      // throw std::exception("Exception");  
   }  
   catch (...) {  
      std::cout << "caught an exception" << std::endl;  
   }  
}  
```