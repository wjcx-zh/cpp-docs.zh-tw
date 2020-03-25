---
title: 編譯器警告 (層級 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: df80bec2294929be463425d74d4bf00421b368e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198428"
---
# <a name="compiler-warning-level-4-c4235"></a>編譯器警告 (層級 4) C4235

使用非標準的擴充：此架構不支援 ' 關鍵字 ' 關鍵字

編譯器不支援您所使用的關鍵字。

此警告會自動升級為錯誤。 如果您想要修改此行為，請使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要讓 C4235 成為層級2警告，請使用下列程式程式碼

```cpp
#pragma warning(2:4235)
```

在原始程式碼檔中。
