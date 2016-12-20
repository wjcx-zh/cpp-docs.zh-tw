---
title: "編譯器錯誤 C2248 | Microsoft Docs"
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
  - "C2248"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2248"
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2248
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : 無法存取類別 'class' 中宣告的 'access' 成員  
  
 衍生類別的成員不能存取基底類別的 `private` 成員。  您無法存取類別執行個體的 `private` 或 `protected` 成員。  
  
 如需 C2248 的詳細資訊，請參閱知識庫 \(Knowledge Base\) 文件 KB243351。  
  
 下列範例會產生 C2248：  
  
```  
// C2248.cpp  
#include <stdio.h>  
class X {  
public:  
   int  m_pubMemb;  
   void setPrivMemb( int i ) {  
      m_privMemb = i;  
      printf_s("\n%d", m_privMemb);  
   }  
protected:  
   int  m_protMemb;  
  
private:  
   int  m_privMemb;  
} x;  
  
int main() {  
   x.m_pubMemb = 4;  
   printf_s("\n%d", x.m_pubMemb);  
   x.m_protMemb = 2;   // C2248 m_protMemb is protected  
   x.m_privMemb = 3;   // C2248  m_privMemb is private  
   x.setPrivMemb(0);   // OK uses public access function  
}  
```  
  
 會讓 C2248 出現的另一個一致性問題是：使用了樣板 friend 和特製化。  如需詳細資訊，請參閱[連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)。  
  
```  
// C2248_b.cpp  
template<class T>  
void f(T t) {  
   t.i;   // C2248  
}  
  
struct S {  
private:  
   int i;  
  
public:  
   S() {}  
   // Delete the following line to resolve.  
   friend void f(S);   // refer to the non-template function void f(S)  
  
   // Uncomment the following line to resolve.  
   // friend void f<S>(S);  
};  
  
int main() {  
   S s;  
   f<S>(s);  
}  
```  
  
 會讓 C2248 出現的另一個一致性問題是：當您嘗試宣告類別的 friend，而在類別範圍中 friend 宣告看不見該類別時。  在這種情況下，請授與封入類別 \(Enclosing Class\) 夥伴關係，以解決這項錯誤。  
  
```  
// C2248_c.cpp  
// compile with: /c  
class T {  
   class S {  
      class E {};  
   };  
   friend class S::E;   // C2248  
};  
  
class A {  
   class S {  
      class E {};  
      friend class A;   // grant friendship to enclosing class  
   };  
   friend class S::E;   // OK  
};  
```