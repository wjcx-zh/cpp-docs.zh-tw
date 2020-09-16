---
title: 編譯器錯誤 C3488
ms.date: 11/04/2016
f1_keywords:
- C3488
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
ms.openlocfilehash: a39c625e63936700661790023a983fa39eeda369
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685788"
---
# <a name="compiler-error-c3488"></a>編譯器錯誤 C3488

預設擷取模式為傳址方式時不允許 'var'

當您指定 Lambda 運算式的預設擷取模式是透過傳址方式時，無法透過傳址方式將變數傳遞給該運算式的 Capture 子句。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 不要將變數明確地傳遞給 Capture 子句，或

- 不要透過傳址方式指定為預設擷取模式，或

- 透過傳值方式指定為預設擷取模式，或

- 透過傳值方式將變數傳遞給 Capture 子句 (這可能會變更 Lambda 運算式的行為)。

## <a name="examples"></a>範例

下列範例會產生 C3488，因為變數 `n` 的參考出現在其預設模式是透過傳址方式之 Lambda 運算式的 Capture 子句：

```cpp
// C3488a.cpp

int main()
{
   int n = 5;
   [&, &n]() { return n; } (); // C3488
}
```

下列範例顯示 C3488 的四種可能解決方式：

```cpp
// C3488b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass &n to the capture clause.
   [&]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-reference as the default capture mode.
   [&n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-value as the default capture mode.
   [=, &n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by value to the capture clause.
   [n]() { return n; } ();
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
