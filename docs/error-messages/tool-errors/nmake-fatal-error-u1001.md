---
title: NMAKE 嚴重錯誤 U1001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1001
dev_langs:
- C++
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4e465af5b4fa22c5f0ba5a9e01ebde0a7ee89e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068139"
---
# <a name="nmake-fatal-error-u1001"></a>NMAKE 嚴重錯誤 U1001

語法錯誤： 不合法的字元 'character' 在巨集

指定的字元會出現在巨集中，但不是字母、 數字或底線。

此錯誤可能被因遺漏冒號巨集展開中：

```
syntax error : illegal character '=' in macro
```