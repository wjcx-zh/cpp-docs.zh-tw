---
title: 嚴重錯誤 1311 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d93aa28d0cef3c07fd469349d485c4009fa4771d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091058"
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