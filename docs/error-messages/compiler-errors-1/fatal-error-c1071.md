---
title: 嚴重錯誤 C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 8fe6b0f3bb1253f72c97f29070ba81cdbdf80508
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166655"
---
# <a name="fatal-error-c1071"></a>嚴重錯誤 C1071

在註解中找到未預期的檔案結尾

編譯器在掃描註解時遇到檔案結尾。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 遺漏註解結束字元 (* /)。

1. 遺漏的原始程式檔的最後一行的註解後的新行字元。

下列範例會產生 C1071:

```
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```