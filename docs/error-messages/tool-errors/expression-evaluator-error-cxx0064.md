---
title: 運算式評估工具錯誤 CXX0064 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b16133484af5a2225f79c5d293a2c8edd948bdb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025889"
---
# <a name="expression-evaluator-error-cxx0064"></a>運算式評估工具錯誤 CXX0064

無法在繫結的虛擬成員函式上設定中斷點

設定中斷點上的虛擬成員函式透過指標至物件，例如：

```
pClass->vfunc( int );
```

可以輸入類別，例如，在虛擬函式上設定中斷點：

```
Class::vfunc( int );
```

此錯誤是與 can0064 相同。