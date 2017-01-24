---
title: "成員函式樣板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式樣板, 成員函式"
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 成員函式樣板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

成員樣板這個詞同時指成員函式樣板和巢狀類別樣板。  成員函式樣板是樣板函式，為類別或類別樣板的成員。  如需詳細資訊，請參閱[巢狀類別樣板](../Topic/Nested%20Class%20Templates.md)。  
  
 成員函式可以是數種內容中的函式樣板。  類別樣板的所有函式都是泛型，但不稱為成員樣板或成員函式樣板。  如果這些成員函式採用自己的樣板引數，則會視為成員函式樣板。  如需詳細資訊，請參閱[樣板類別的成員函式](../Topic/Member%20Functions%20of%20Template%20Classes.md)。  
  
## 範例  
 非樣板或樣板類別的成員函式樣板會宣告為函式樣板，並且包含其樣板參數。  
  
```  
// member_function_templates.cpp  
struct X  
{  
   template <class T> void mf(T* t) {}  
};  
  
int main()  
{  
   int i;  
   X* x = new X();  
   x->mf(&i);  
}  
```  
  
## 範例  
 下列範例將示範樣板類別的成員函式樣板。  
  
```  
// member_function_templates2.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u)  
   {  
   }  
};  
  
int main()  
{  
}  
```  
  
## 範例  
 此外，在 Visual Studio .NET 2003 \(含\) 以後版本中，成員樣板也可以在類別之外定義。  
  
```  
// defining_member_templates_outside_class.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u);  
};  
  
template<typename T> template <typename U>  
void X<T>::mf(const U &u)  
{  
}  
  
int main()  
{  
}  
```  
  
## 範例  
 區域類別不可以有成員樣板。  
  
 成員樣板函式不可以是虛擬函式，而且宣告時的名稱與基底類別虛擬函式相同時，不可覆寫來自基底類別的虛擬函式。  
  
 Visual C\+\+ .NET 2003 已引入樣板化使用者定義轉換的支援。  下列範例依標準所指定，可在 Visual C\+\+ .NET 2003 中運作。  
  
```  
// templated_user_defined_conversions.cpp  
template <class T>  
struct S  
{  
   template <class U> operator S<U>()  
   {  
      return S<U>();  
   }  
};  
  
int main()  
{  
   S<int> s1;  
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.  
}  
```  
  
## 請參閱  
 [函式樣板](../cpp/function-templates.md)