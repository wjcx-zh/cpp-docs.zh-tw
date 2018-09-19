---
title: 編譯器警告 （層級 1） C4350 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad49a7471be257fa0c22f66fa1bb2bbea049194
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096687"
---
# <a name="compiler-warning-level-1-c4350"></a>編譯器警告 (層級 1) C4350

行為變更: 呼叫了 'member1' 而不是 'member2'

右值無法繫結至非 const 的參考。 在 Visual Studio 2003 之前的 Visual c + + 版本中，則可以將變數繫結到直接初始化中的非 const 參考。 此程式碼現在會發出警告。

回溯相容性，仍可將右值繫結到非 const 的參考，但可能的情況下，會偏好標準轉換。

這則警告表示 Visual c + +.NET 2002年的編譯器行為的變更。 如果啟用，那麼這個警告可能可能給正確的程式碼。 比方說，它無法提供使用時**std::auto_ptr**類別樣板。

如果您收到這則警告，請檢查您的程式碼，以查看是否相依於繫結至非 const 參考的右值。 將常數新增至參考，或提供其他的 const 參考多載可能會解決此問題。

此警告預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

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