---
title: "private (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "private_cpp"
  - "private"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "private 關鍵字 [C++]"
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# private (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
private:  
   [member-list]  
private base-class  
```  
  
## 備註  
 `private` 關鍵字加在類別成員清單前面時，會指定只能從成員函式和類別的 friend 存取這些成員。  這種做法適用於在下一個存取指定名稱或類別結尾之前宣告的所有成員。  
  
 `private` 關鍵字加在基底類別的名稱前面時，會將基底類別的 public 和 protected 成員指定為衍生類別的 private 成員。  
  
 類別中成員的預設存取方式是 private。  結構或等位中成員的預設存取方式是 public。  
  
 對於類別而言，基底類別的預設存取方式為 private，對於結構而言則為 public。  等位不可以具有基底類別。  
  
 如需相關資訊，請參閱 [friend](../cpp/friend-cpp.md)、[public](../cpp/public-cpp.md)、[protected](../cpp/protected-cpp.md) 和[控制對類別成員的存取](../misc/controlling-access-to-class-members.md)中的成員存取表。  
  
## \/clr 專屬資訊  
 在 CLR 類型中，C\+\+ 存取指定名稱關鍵字 \(**public**、`private` 和 `protected`\) 可能會影響類型和方法在組件方面的可視性。  如需詳細資訊，請參閱[類型和成員可視性](../misc/type-and-member-visibility.md)。  
  
> [!NOTE]
>  以 [\/LN](../build/reference/ln-create-msil-module.md) 編譯的檔案不受這個行為影響。  在這種情況下，所有 Managed 類別 \(public 或 private\) 都會是可見。  
  
## \/clr 專屬資訊結束  
  
## 範例  
  
```  
// keyword_private.cpp  
class BaseClass {  
public:  
   // privMem accessible from member function  
   int pubFunc() { return privMem; }  
private:  
   void privMem;  
};  
  
class DerivedClass : public BaseClass {  
public:  
   void usePrivate( int i )  
      { privMem = i; }   // C2248: privMem not accessible  
                         // from derived class  
};  
  
class DerivedClass2 : private BaseClass {  
public:  
   // pubFunc() accessible from derived class  
   int usePublic() { return pubFunc(); }  
};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   DerivedClass2 aDerived2;  
   aBase.privMem = 1;     // C2248: privMem not accessible  
   aDerived.privMem = 1;  // C2248: privMem not accessible  
                          //    in derived class  
   aDerived2.pubFunc();   // C2247: pubFunc() is private in  
                          //    derived class  
}  
```  
  
## 請參閱  
 [控制對類別成員的存取](../misc/controlling-access-to-class-members.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)