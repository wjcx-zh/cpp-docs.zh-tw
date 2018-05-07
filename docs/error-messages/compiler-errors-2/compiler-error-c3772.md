---
title: 編譯器錯誤 C3772 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3772
dev_langs:
- C++
helpviewer_keywords:
- C3772
ms.assetid: 63e938d4-088d-41cc-a562-5881a05b5710
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01003a4d474b80c152d271546f659d418f3c4df7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>另請參閱  
[範本](../../cpp/templates-cpp.md)   
[範本特製化](../../cpp/template-specialization-cpp.md)   
