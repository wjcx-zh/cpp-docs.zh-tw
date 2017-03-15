---
title: "編譯器錯誤 C3535 | Microsoft Docs"
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
  - "C3535"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3535"
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3535
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法從 'type2' 推算 'type1' 的型別  
  
 無法從初始化運算式的型別來推算由 `auto` 關鍵字所宣告之變數的型別。  例如，如果初始化運算式評估為不是型別的 `void`，便會發生這個錯誤。  
  
### 更正這個錯誤  
  
1.  確定初始化運算式的型別不是 `void`。  
  
2.  確定宣告不是主要資料型別 \(Fundamental Type\) 的指標。  如需詳細資訊，請參閱[基本類型](../../cpp/fundamental-types-cpp.md)。  
  
3.  確定當宣告是型別的指標時，初始化運算式為指標型別。  
  
## 範例  
 下列範例會產生 C3535 錯誤，因為初始化運算式會評估成 `void`。  
  
```  
// C3535a.cpp  
// Compile with /Zc:auto  
void f(){}  
int main()  
{  
   auto x = f();   //C3535  
   return 0;  
}  
```  
  
## 範例  
 下列範例會產生 C3535 錯誤，因為陳述式將變數 `x` 宣告為所推算型別的指標，但是初始化運算式的型別為 double。  因此，編譯器無法推算變數的型別。  
  
```  
// C3535b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto* x = 123.0;   // C3535  
   return 0;  
}  
```  
  
## 範例  
 下列範例會產生 C3535 錯誤，因為變數 `p` 宣告為所算斷型別的指標，但是初始化運算式不是指標型別。  
  
```  
// C3535c.cpp  
// Compile with /Zc:auto  
class A { };  
A x;  
auto *p = x;  // C3535  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)   
 [基本類型](../../cpp/fundamental-types-cpp.md)