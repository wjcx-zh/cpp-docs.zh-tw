---
title: 編譯器警告 (層級 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 5e23e6aa69fe8a59e3dfd22af7e33780c223cdd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401601"
---
# <a name="compiler-warning-level-3-c4686"></a>編譯器警告 (層級 3) C4686

> '*使用者定義型別*': 行為可能變更，在 UDT 傳回呼叫慣例

## <a name="remarks"></a>備註

類別樣板特製化不是之前曾在傳回的型別定義。 具現化類別的任何項目將解決 C4686;宣告執行個體，或存取的成員 (C\<int >:: 任何項目) 也是選項。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

## <a name="example"></a>範例

請改嘗試為下列：

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```