---
title: "編譯器錯誤 C3225 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3225"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3225"
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器錯誤 C3225
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'arg' 的泛型型別引數不可為 'type'，它必須是實值型別或控制代碼型別  
  
 泛型型別引數不是正確型別。  
  
 如需詳細資訊，請參閱[Generics](../../windows/generics-cpp-component-extensions.md)。  
  
## 範例  
 您不能以原生型別具現化泛型型別。  下列範例會產生 C3225。  
  
```  
// C3225.cpp  
// compile with: /clr  
class A {};  
  
ref class B {};  
  
generic <class T>  
ref class C {};  
  
int main() {  
   C<A>^ c = gcnew C<A>;   // C3225  
   C<B^>^ c2 = gcnew C<B^>;   // OK  
}  
```  
  
## 範例  
 下列範例會使用 C\# 建立元件。  請注意，條件約束指定泛型型別只能以實值型別具現化。  
  
```  
// C3225_b.cs  
// compile with: /target:library  
// a C# program  
public class MyList<T> where T: struct {}  
```  
  
## 範例  
 這個範例使用了 C\# 設計的元件，而違反了在 <xref:System.Nullable> 之外，MyList 只能以實值型別具現化的條件約束。  下列範例會產生 C3225。  
  
```  
// C3225_c.cpp  
// compile with: /clr  
#using "C3225_b.dll"  
ref class A {};  
value class B {};  
int main() {  
   MyList<A> x;   // C3225  
   MyList<B> y;   // OK  
}  
```