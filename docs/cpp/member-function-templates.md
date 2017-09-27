---
title: "成員函式樣板 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: f460497071445cff87308fa9bf6e0d43c6f13a3e
ms.openlocfilehash: bba7b35c08fbc171ddbb4c572285c0aed2f58a3b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="member-function-templates"></a>成員函式樣板

成員樣板這個詞同時指成員函式樣板和巢狀類別樣板。 成員函式樣板是樣板函式，為類別或類別樣板的成員。  
  
 成員函式可以是數種內容中的函式樣板。 類別樣板的所有函式都是泛型，但不稱為成員樣板或成員函式樣板。 如果這些成員函式採用自己的樣板引數，則會視為成員函式樣板。  
  
## <a name="example"></a>範例

 非樣板或樣板類別的成員函式樣板會宣告為函式樣板，並且包含其樣板參數。  
  
```cpp
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
  
## <a name="example"></a>範例

 下列範例將示範樣板類別的成員函式樣板。  
  
```cpp
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
  
## <a name="example"></a>範例

 此外，在 Visual Studio.NET 2003年和更新版本，也可以定義成員樣板類別之外。  
  
```cpp
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
  
## <a name="example"></a>範例

 區域類別不可以有成員樣板。  
  
 成員樣板函式不可以是虛擬函式，而且宣告時的名稱與基底類別虛擬函式相同時，不可覆寫來自基底類別的虛擬函式。  
  
 Visual c + +.NET 2003 中引入樣板化的使用者定義轉換的支援。 下列範例依標準所指定，可在 Visual C++ .NET 2003 中運作。  
  
```cpp
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
  
## <a name="see-also"></a>另請參閱

 [函式樣板](../cpp/function-templates.md)

