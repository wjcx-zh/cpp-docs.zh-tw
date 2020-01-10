---
title: 編譯器警告（層級4） C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: ceb7e65a292e5b9e9ef960ca9553183b703c93f0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991692"
---
# <a name="compiler-warning-level-4-c4001"></a>編譯器警告（層級4） C4001

使用了非標準的擴充功能「單行批註」

> [!NOTE]
> Visual Studio 2017 15.5 版中會移除此警告，因為單行批註在 C99 中是標準的。

單行批註是標準，在C++ C 中則是標準（從 C99 開始）。
在嚴格的 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）、包含單行批註的 C 檔案底下，由於使用非標準的延伸模組，因此會產生 C4001。 因為單行批註是中C++的標準，所以使用 Microsoft extensions （/ze）進行編譯時，包含單行批註的 C 檔案不會產生 C4001。

## <a name="example"></a>範例

若要停用警告，請取消批註[#pragma 警告（disable：4001）](../../preprocessor/warning.md)。

```cpp
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```
