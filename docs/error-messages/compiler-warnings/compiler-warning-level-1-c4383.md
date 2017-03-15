---
title: "編譯器警告 (層級 1) C4383 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4383"
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'instance\_dereference\_operator' : 如果有使用者定義的 'operator' 運算子，控制代碼取值的含意可能會變更，請將這個運算子撰寫成對運算元很明確的靜態函式  
  
 當您在 Managed 型別中加入取值運算子的使用者定義執行個體覆寫時，很可能就會覆寫掉型別的取值運算子傳回控制代碼物件的功能。  請考慮撰寫靜態的使用者定義取值運算子。  
  
 如需詳細資訊，請參閱[物件控制代碼運算子 \(^\)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md)與[Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
 而且，其他語言編譯器也不能經由參考的中繼資料使用執行個體運算子。  如需詳細資訊，請參閱[使用者定義的運算子](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C4383。  
  
```  
// C4383.cpp  
// compile with: /clr /W1  
  
ref struct S {  
   int operator*() { return 0; }   // C4383  
};  
  
ref struct T {  
   static int operator*(T%) { return 0; }  
};   
  
int main() {  
   S s;  
   S^ pS = %s;  
  
   T t;  
   T^ pT = %t;  
   T% rT = *pT;  
}  
```