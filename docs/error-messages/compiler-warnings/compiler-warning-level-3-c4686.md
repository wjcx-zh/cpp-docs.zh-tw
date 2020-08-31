---
title: 編譯器警告 (層級 3) C4686
description: Microsoft c + + 編譯器警告 C4686。
ms.date: 08/29/2020
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 6886ae7f413de630457b53e85b5cd75c4542ee19
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194493"
---
# <a name="compiler-warning-level-3-c4686"></a>編譯器警告 (層級 3) C4686

> 「*使用者定義型*別」：行為中的可能變更，UDT 傳回呼叫慣例中的變更

## <a name="remarks"></a>備註

類別樣板特製化在傳回型別中使用之前未定義。 具現化類別的任何作業都會解析 C4686;例如，宣告實例或存取成員 (例如， `C<int>::some_member`) 也是選項。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

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
