---
title: "已被取代 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- deprecated_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
caps.latest.revision: 9
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
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 9ac25648e2d19da82f6c213992699c237e05c01e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="deprecated-c"></a>deprecated (C++)
本主題是關於 Microsoft 專有 declspec 宣告已被取代。 如需 C + + 14`[[deprecated]]`屬性，以及何時使用與 Microsoft 專有 declspec 或 pragma，該屬性的指導方針請參閱[c + + 標準屬性](attributes2.md)。

 下面，例外狀況**取代**宣告可提供相同的功能[已被取代](../preprocessor/deprecated-c-cpp.md)pragma:  
  
-   **取代**宣告可讓您指定特定形式的函式多載，為已被取代，而 pragma 形式會套用至所有的多載形式的函式名稱。  
  
-   **取代**宣告可讓您指定將會在編譯時期顯示的訊息。 訊息的文字可以來自巨集。  
  
-   巨集，才可以標示為已被取代的**取代**pragma。  
  
 如果編譯器遇到取代識別項或標準使用[ `[[deprecated]]` ](attributes2.md)屬性[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)警告就會擲回。  
  
## <a name="example"></a>範例  
 下列範例將示範使用 deprecated 函式時，如何將函式標示為取代以及如何指定要在編譯時期顯示的訊息。  
  
```  
// deprecated.cpp  
// compile with: /W3  
#define MY_TEXT "function is deprecated"  
void func1(void) {}  
__declspec(deprecated) void func1(int) {}  
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}  
__declspec(deprecated(MY_TEXT)) void func3(int) {}  
  
int main() {  
   func1();  
   func1(1);   // C4996  
   func2(1);   // C4996  
   func3(1);   // C4996  
}  
```  
  
## <a name="example"></a>範例  
 下列範例將示範使用 deprecated 類別時，如何將類別標示為取代以及如何指定要在編譯時期顯示的訊息。  
  
```  
// deprecate_class.cpp  
// compile with: /W3  
struct __declspec(deprecated) X {  
   void f(){}  
};  
  
struct __declspec(deprecated("** X2 is deprecated **")) X2 {  
   void f(){}  
};  
  
int main() {  
   X x;   // C4996  
   X2 x2;   // C4996  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)
