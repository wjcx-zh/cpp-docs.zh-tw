---
title: 編譯器警告 (層級 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 314ee068fb2be6148304360b0aaa3bd8029c283b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401068"
---
# <a name="compiler-warning-level-4-c4234"></a>編譯器警告 (層級 4) C4234

使用非標準擴充： 保留供未來使用的 'keyword' 關鍵字

編譯器尚未實作您所用的關鍵字。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要 C4234 變成是層級 4 警告的問題，

```
#pragma warning(2:4234)
```

在您的原始程式碼檔。