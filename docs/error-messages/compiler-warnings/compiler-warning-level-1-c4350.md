---
title: 編譯器警告 (層級 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 890ecd4fcec1212fa04a58b0eaab8c2eb4206763
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187215"
---
# <a name="compiler-warning-level-1-c4350"></a>編譯器警告 (層級 1) C4350

行為變更: 呼叫了 'member1' 而不是 'member2'

右值無法系結至非 const 參考。 在 Visual Studio 2003 之前C++的 Visual 版本中，可以在直接初始化中將右值系結至非 const 參考。 這段程式碼現在會提供警告。

為了回溯相容性，仍然可以將右值系結至非 const 參考，但可能的話，建議您盡可能進行標準轉換。

此警告代表來自 Visual C++ .net 2002 編譯器的行為變更。 若已啟用，可能會為正確的程式碼提供此警告。 例如，使用**std：： auto_ptr**類別範本時，可以提供它。

如果您收到此警告，請檢查您的程式碼，以查看它是否相依于將右值系結至非 const 參考。 將 const 新增至參考或提供額外的 const 參考多載，可能會解決此問題。

此警告預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

下列範例會產生 C4350：

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
