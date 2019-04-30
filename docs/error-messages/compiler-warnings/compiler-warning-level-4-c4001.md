---
title: 編譯器警告 （層級 4） C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: dd18dc27ee13eab05ea0253c8ebcc990105c15c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401484"
---
# <a name="compiler-warning-level-4-c4001"></a>編譯器警告 （層級 4） C4001

使用非標準的擴充 '單行註解'

> [!NOTE]
> 這個警告會移除 Visual Studio 2017 15.5 版中，因為單行註解是在 C99 標準。

單行註解是在標準C++和 C 啟動與 C99 標準。
嚴格的 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，C 的檔案，其中包含單行註解，產生 C4001 由於非標準的擴充功能的使用方式。 由於單行註解中的標準C++、 C 檔案包含單行註解不會產生 C4001 搭配 Microsoft 擴充功能 (/Ze) 進行編譯時。

## <a name="example"></a>範例

若要停用警告，請取消註解[#pragma warning(disable:4001)](../../preprocessor/warning.md)。

```
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```