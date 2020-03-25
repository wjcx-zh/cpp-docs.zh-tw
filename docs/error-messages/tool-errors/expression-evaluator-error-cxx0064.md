---
title: 運算式評估工具錯誤 CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: f763754299ed9257fb909b49a7a19c6f3ad58681
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184459"
---
# <a name="expression-evaluator-error-cxx0064"></a>運算式評估工具錯誤 CXX0064

無法在系結的虛擬成員函式上設定中斷點

已透過物件的指標在虛擬成員函式上設定中斷點，例如：

```
pClass->vfunc( int );
```

您可以藉由輸入類別，在虛擬函式上設定中斷點，例如：

```
Class::vfunc( int );
```

此錯誤與 CAN0064 相同。
