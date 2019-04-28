---
title: 編譯器警告 (層級 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: 1948bdec5367fa7943f5a0de4338fd4ecd6c6581
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220503"
---
# <a name="compiler-warning-level-4-c4564"></a>編譯器警告 (層級 4) C4564

方法 'method' 的類別 'class' 定義不支援的預設參數 'parameter'

編譯器偵測到具有一或多個參數具有預設值的方法。 叫用方法時，將忽略參數的預設值明確指定這些參數的值。 如果您未明確指定這些參數的值C++編譯器會產生錯誤。

使用 Visual Basic 建立下列.dll 的情況下，指定允許預設參數方法引數：

```
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

與下列C++使用 Visual Basic 中，以建立此.dll 檔的範例

```
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