---
title: "編譯器錯誤 C3409 | Microsoft Docs"
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
  - "C3409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3409"
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3409
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允許空白的屬性區塊  
  
 編譯器將方括弧當做[屬性](../../windows/cpp-attributes-reference.md)區塊編譯，但找不到屬性。  
  
 當您使用方括號做為 Lambda 運算式定義的一部分時，編譯器可能會產生這個錯誤。  當編譯器無法判斷方括號是 Lambda 運算式定義的還是屬性區塊的一部分時，就會發生這個錯誤。  如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)。  
  
### 更正這個錯誤  
  
1.  如果方括號是屬性區塊的一部分：  
  
    1.  在屬性區塊中提供一個或多個屬性。  
  
    2.  移除屬性區塊。  
  
2.  如果方括號是 Lambda 運算式的一部分：  
  
    1.  確定 Lambda 運算式遵循有效的語法規則。  
  
         如需 Lambda 運算式語法的詳細資訊，請參閱 [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)。  
  
## 範例  
 下列範例會產生 C3409 錯誤。  
  
```  
// C3409.cpp  
// compile with: /c  
#include <windows.h>  
[]   // C3409  
class a {};  
  
// OK  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface x {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class b : public x {};  
```  
  
## 範例  
 下列範例會產生 C3409 錯誤，因為 Lambda 運算式使用 `mutable` 規格，但是沒有提供參數清單。  編譯器無法判斷方括號是 Lambda 運算式定義的還是屬性區塊的一部分。  
  
```  
// C3409b.cpp  
  
int main()  
{  
   [] mutable {}();  
}  
```  
  
## 請參閱  
 [屬性](../../windows/cpp-attributes-reference.md)   
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)   
 [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)