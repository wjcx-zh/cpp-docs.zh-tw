---
title: "編譯器警告 （層級 1） C4350 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 141f5552c4b86e170587f42ebabf5e2e597b4e96
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4350"></a>編譯器警告 (層級 1) C4350
行為變更: 呼叫了 'member1' 而不是 'member2'  
  
 右值無法繫結至非 const 的參考。 在 Visual Studio 2003 之前的 Visual c + + 版本中，它是可以繫結到非 const 參考直接初始化中的右值。 此程式碼現在會發出警告。  
  
 回溯相容性，仍然可以將右值繫結至非 const 的參考，但可能的情況下，標準轉換是慣用。  
  
 這個警告表示 Visual c + +.NET 2002年編譯器的行為變更。 如果啟用，那麼這個警告可能可能給正確的程式碼。 例如，無法授與它使用時**std::auto_ptr**類別樣板。  
  
 如果您收到這個警告，請檢查您的程式碼，以查看取決於其繫結至非 const 參考的右值。 加入 const 的參考，或提供其他的 const 參考多載可能會解決這個問題。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱[編譯器警告為關閉的預設](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4350:  
  
```cpp  
// C4350.cpp  
// compile with: /W1  
#pragma warning (default : 4350)  
class A {};  
  
class B  
{  
public:  
   B(B&){}  
   // try the following instead:  
   // B(const B&){}  
  
   B(A){}  
   operator A(){ return A();}  
};  
  
B source() { return A(); }  
  
int main()  
{  
   B ap(source());   // C4350  
}  
```
