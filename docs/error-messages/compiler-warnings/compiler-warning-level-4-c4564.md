---
title: 編譯器警告 (層級 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: f5db6bf366c86a716be33539feb0085ac03a9647
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683168"
---
# <a name="compiler-warning-level-4-c4564"></a>編譯器警告 (層級 4) C4564

類別 ' class ' 的方法 ' method ' 定義了不支援的預設參數 ' parameter '

編譯器偵測到具有一或多個參數的方法，其具有預設值。 叫用方法時，將會忽略參數的預設值;明確指定這些參數的值。 如果您未明確指定這些參數的值， C++編譯器會產生錯誤。

假設下列使用 Visual Basic 建立的 .dll，它允許方法引數上的預設參數：

```vb
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

下列C++範例會使用以 Visual Basic 建立的 .dll，

```cpp
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```