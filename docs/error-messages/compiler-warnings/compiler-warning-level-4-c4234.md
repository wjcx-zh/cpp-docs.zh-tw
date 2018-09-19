---
title: 編譯器警告 （層級 4） C4234 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4234
dev_langs:
- C++
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6ce6ba622cb480096144706589a01dee7326f38
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118228"
---
# <a name="compiler-warning-level-4-c4234"></a>編譯器警告 (層級 4) C4234

使用非標準擴充： 保留供未來使用的 'keyword' 關鍵字

編譯器尚未實作您所用的關鍵字。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要 C4234 變成是層級 4 警告的問題，

```
#pragma warning(2:4234)
```

在您的原始程式碼檔。