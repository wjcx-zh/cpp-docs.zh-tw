---
title: "編譯器警告 (層級 1) C4946 | Microsoft Docs"
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
  - "C4946"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4946"
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4946
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在關聯的類別之間使用的 reinterpret\_cast：'class1' 和 'class2'  
  
 請不要使用[reinterpret\_cast](../../cpp/reinterpret-cast-operator.md) 在相關的型別之間做轉換。  請改用 [static\_cast](../../cpp/static-cast-operator.md) ，或為多型型別而改用 [dynamic\_cast](../../cpp/dynamic-cast-operator.md)。  
  
 在預設情況下此警告為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列程式碼範例會產生 C4946：  
  
```  
// C4946.cpp  
// compile with: /W1  
#pragma warning (default : 4946)  
class a {  
public:  
   a() : m(0) {}  
   int m;  
};  
  
class b : public virtual a {  
};  
  
class b2 : public virtual a {  
};  
  
class c : public b, public b2 {  
};  
  
int main() {  
   c* pC = new c;  
   a* pA = reinterpret_cast<a*>(pC);   // C4946  
   // try the following line instead  
   // a* pA = static_cast<a*>(pC);  
}  
```