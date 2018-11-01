---
title: 嚴重錯誤 1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: ba2b797c9bf521533e7c2ccff8d358b6216d392f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637901"
---
# <a name="fatal-error-c1311"></a>嚴重錯誤 1311

COFF 格式無法以靜態方式初始化 'var'，與數字的位元組的位址

在編譯時期不知道其值的位址無法以靜態方式指派給變數，其型別具有少於四個位元組的儲存體。

會發生此錯誤的程式碼，否則為有效的 c + +。

下列範例示範了一種可能會造成 C1311 的情況。

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```