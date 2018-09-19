---
title: 嚴重錯誤 C1071 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1071
dev_langs:
- C++
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4487de60148e1da7668bc44c996c5dfb955a9d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033000"
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