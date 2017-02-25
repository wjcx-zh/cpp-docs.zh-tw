---
title: "編譯器錯誤 C3821 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3821"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3821"
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器錯誤 C3821
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 在 Unmanaged 函式中不可以使用 Managed 型別或函式  
  
 搭配內嵌組件或 [setjmp](../../c-runtime-library/reference/setjmp.md) 的函式不可包含實值型別或 Managed 類別。  若要修正這項錯誤，請移除內嵌組譯碼和 `setjmp` 或移除 Managed 物件。  
  
 如果嘗試要在 vararg 函式中使用自動儲存，也可能會發生 C3821。如需詳細資訊，請參閱[Variable Argument Lists \(...\) \(C\+\+\/CLI\)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)與[參考類型的 C\+\+ 堆疊語意](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## 範例  
 下列範例會產生 C3821。  
  
```  
// C3821a.cpp  
// compile with: /clr /c  
public ref struct R {};  
void test1(...) {  
   R r;   // C3821  
}  
```  
  
## 範例  
 下列範例會產生 C3821。  
  
```  
// C3821b.cpp  
// compile with: /clr  
// processor: /x86  
ref class A {  
   public:  
   int i;  
};  
  
int main() {  
   // cannot use managed classes in this function  
   A ^a;     
  
   __asm {  
      nop  
   }  
} // C3821  
```  
  
## 範例  
 下列範例會產生 C3821。  
  
```  
// C3821c.cpp  
// compile with: /clr:oldSyntax  
// processor: /x86  
__gc  class A {  
   public:  
   int i;  
};  
  
int main() {  
   // cannot use managed classes in this function  
   A *a;     
  
   __asm {  
      nop  
   }  
} // C3821  
```