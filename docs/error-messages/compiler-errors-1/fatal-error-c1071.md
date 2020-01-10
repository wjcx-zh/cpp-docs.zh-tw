---
title: 嚴重錯誤 C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 2f39359d55b5564c6379c84f07e942cf3484e011
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747406"
---
# <a name="fatal-error-c1071"></a>嚴重錯誤 C1071

在註解中找到未預期的檔案結尾

編譯器在掃描批註時已到達檔案結尾。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 遺漏批註結束字元（*/）。

1. 原始程式檔最後一行的批註後面遺漏分行符號。

下列範例會產生 C1071：

```cpp
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```
