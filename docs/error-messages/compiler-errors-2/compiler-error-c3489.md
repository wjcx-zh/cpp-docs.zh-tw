---
title: 編譯器錯誤 C3489
ms.date: 11/04/2016
f1_keywords:
- C3489
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
ms.openlocfilehash: d2ba8d919ab71b566950cc227588e071d24016bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381100"
---
# <a name="compiler-error-c3489"></a>編譯器錯誤 C3489

預設擷取模式為傳值方式時需要 'var'

當您指定 Lambda 運算式的預設擷取模式是透過傳值方式時，無法透過傳值方式將變數傳遞給該運算式的 Capture 子句。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 不要將變數明確地傳遞給 Capture 子句，或

- 不要透過傳值方式指定為預設擷取模式，或

- 透過傳址方式指定為預設擷取模式，或

- 透過傳址方式將變數傳遞給 Capture 子句 (這可能會變更 Lambda 運算式的行為)。

## <a name="example"></a>範例

下列範例會產生 C3489，因為變數 `n` 是透過傳值方式出現在其預設模式為透過傳值方式之 Lambda 運算式的 Capture 子句中：

```
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

## <a name="example"></a>範例

下列範例顯示 C3489 的四種可能解決方式：

```
// C3489b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass n to the capture clause.
   [=]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-value as the default capture mode.
   [n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-reference as the default capture mode.
   [&, n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by reference to the capture clause.
   [&n]() { return n; } ();
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)