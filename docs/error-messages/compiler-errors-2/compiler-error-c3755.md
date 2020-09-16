---
title: 編譯器錯誤 C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: cc4e5423dc8fc53a8f749e2392ff23658a0cb0f1
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685111"
---
# <a name="compiler-error-c3755"></a>編譯器錯誤 C3755

' delegate '：可能無法定義委派

可以宣告但未定義 [ (c + + 元件延伸模組) 的委派 ](../../extensions/delegate-cpp-component-extensions.md) 。

## <a name="examples"></a>範例

下列範例會產生 C3755。

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

如果您嘗試建立委派範本，也可能會發生 C3755。 下列範例會產生 C3755。

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
