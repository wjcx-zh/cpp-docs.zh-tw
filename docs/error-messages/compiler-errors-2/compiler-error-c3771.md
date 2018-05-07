---
title: 編譯器錯誤 C3771 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3771
dev_langs:
- C++
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8adfdb1562cc9efbe208bd7c887b7c4aa77ddd82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3771"></a>編譯器錯誤 C3771
"identifier"：在最接近的命名空間範圍內找不到 friend 宣告  
  
在目前命名空間內找不到指定範本 *識別碼* 的類別樣板宣告。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確認目前命名空間中有定義樣板識別項的類別樣板宣告，或樣板識別項是完整名稱。  
  
## <a name="example"></a>範例  
下列程式碼範例在命名空間 `NA`中宣告類別樣板和函式，但嘗試在命名空間 `NB`中宣告 friend 函式樣板。  
  
```cpp  
// C3771.cpp   
// compile with: /c  
  
namespace NA {  
template<class T> class A {  
    void aFunction(T t) {};  
    };  
}  
// using namespace NA;  
namespace NB {  
    class X {  
        template<class T> friend void A<T>::aFunction(T); // C3771  
// try the following line instead  
//      template<class T> friend void NA::A<T>::aFunction(T);  
// or try "using namespace NA;" instead.  
    };  
}  
```  
  
## <a name="see-also"></a>另請參閱  
[範本](../../cpp/templates-cpp.md)  