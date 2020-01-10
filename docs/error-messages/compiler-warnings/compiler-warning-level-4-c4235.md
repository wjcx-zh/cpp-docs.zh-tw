---
title: 編譯器警告 (層級 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 3e3cb2e40ed42b24ee52252003b26ec09cd86710
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541765"
---
# <a name="compiler-warning-level-4-c4235"></a>編譯器警告 (層級 4) C4235

使用非標準的擴充：此架構不支援 ' 關鍵字 ' 關鍵字

編譯器不支援您所使用的關鍵字。

此警告會自動升級為錯誤。 如果您想要修改此行為，請使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要讓 C4235 成為層級2警告，請使用下列程式程式碼

```cpp
#pragma warning(2:4235)
```

在原始程式碼檔中。