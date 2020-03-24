---
title: 編譯器警告 (層級 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: a8eae1ddeb875d267b82c67e989cb41e8c9b2afb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185447"
---
# <a name="compiler-warning-level-3-c4686"></a>編譯器警告 (層級 3) C4686

> '*使用者定義類型*'：行為的可能變更，UDT 傳回呼叫慣例中的變更

## <a name="remarks"></a>備註

在傳回型別中使用類別樣板特製化之前，尚未定義它。 任何具現化類別的專案都會解析 C4686;宣告實例或存取成員（C\<int >：：任何專案）也是選項。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

## <a name="example"></a>範例

請改為嘗試下列動作：

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
