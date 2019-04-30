---
title: 編譯器警告 (層級 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 80ad388b26b2b972aa1301c1f335d0361a75f15f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401042"
---
# <a name="compiler-warning-level-4-c4235"></a>編譯器警告 (層級 4) C4235

使用非標準擴充: 'keyword' 關鍵字不支援這種架構

編譯器不支援您使用的關鍵字。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要將層級 2 警告 c4235，使用下列程式碼行

```
#pragma warning(2:4235)
```

在您的原始程式碼檔。