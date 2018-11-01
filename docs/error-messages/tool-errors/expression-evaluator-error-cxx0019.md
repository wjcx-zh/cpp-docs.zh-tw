---
title: 運算式評估工具錯誤 CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 266e97f28cf0f27cb87e9743399c66aba87c0e8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658090"
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