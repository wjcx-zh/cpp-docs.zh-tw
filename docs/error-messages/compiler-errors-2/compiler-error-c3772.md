---
title: "編譯器錯誤 C3772 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3772
dev_langs:
- C++
helpviewer_keywords:
- C3772
ms.assetid: 63e938d4-088d-41cc-a562-5881a05b5710
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3290a3be06ecc223bfc87e39ed068d187d4f95c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3772"></a>編譯器錯誤 C3772
"name"：無效的 friend 樣板宣告  
  
類別樣板特製化的 friend 宣告無效。 您無法宣告類別樣板的明確或部分特製化，又在相同的陳述式中宣告該特製化的 friend。 *name* 預留位置識別無效的宣告。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請勿宣告類別樣板特製化的 friend。  
  
-   如果應用程式適用的話，您可以宣告類別樣板的 friend，或宣告特定的部分或明確特製化的 friend。  
  
## <a name="example"></a>範例  
 下列程式碼範例失敗，因為它會宣告類別樣板之部分特製化的 friend。  
  
```cpp  
// c3772.cpp  
// compile with: /c  
  
// A class template.  
    template<class T> class A {};  
  
// A partial specialization of the class template.  
    template<class T> class A<T*> {};  
  
// An explicit specialization.  
    template<> class A<char>;  
  
class X {  
// Invalid declaration of a friend of a partial specialization.  
    template<class T> friend class A<T*>; // C3772  
  
// Instead, if it is appropriate for your application, declare a   
// friend of the class template. Consequently, all specializations   
// of the class template are friends:  
//    template<class T> friend class A;  
// Or declare a friend of a particular partial specialization:  
//    friend class A<int*>;  
// Or declare a friend of a particular explicit specialization:  
//    friend class A<char>;  
};  
```  
  
## <a name="see-also"></a>請參閱  
[範本](../../cpp/templates-cpp.md)   
[樣板特製化](../../cpp/template-specialization-cpp.md)   
