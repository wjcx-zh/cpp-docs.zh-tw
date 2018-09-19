---
title: 編譯器警告 （層級 4） C4001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4001
dev_langs:
- C++
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c325656b9e61ee324a3b9f171413f1020440f9ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025408"
---
# <a name="compiler-warning-level-4-c4001"></a>編譯器警告 （層級 4） C4001

使用非標準的擴充 '單行註解'

> [!NOTE]
> 這個警告會移除 Visual Studio 2017 15.5 版中，因為單行註解是在 C99 標準。

單行註解是 standard c + + 和 C 啟動與 C99 標準。
嚴格的 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，C 的檔案，其中包含單行註解，產生 C4001 由於非標準的擴充功能的使用方式。 由於單行註解是標準 c + + 中，C 檔案包含單行註解不會產生 C4001 搭配 Microsoft 擴充功能 (/Ze) 進行編譯時。

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