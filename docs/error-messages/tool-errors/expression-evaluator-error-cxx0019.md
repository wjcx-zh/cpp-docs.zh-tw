---
title: 運算式評估工具錯誤 CXX0019 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fba76b75c640917b3b99cd41500d682cb1b32f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031804"
---
# <a name="expression-evaluator-error-cxx0019"></a>運算式評估工具錯誤 CXX0019

不正確的類型轉換

C 運算式評估工具無法執行轉換所寫的型別。

此錯誤是與 can0019 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 指定的型別是未知的。

1. 沒有指標類型的層級太多。 例如，類型轉換

    ```
    (char **)h_message
    ```

     無法評估 C 運算式評估工具。