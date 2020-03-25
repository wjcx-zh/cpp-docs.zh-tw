---
title: 運算式評估工具錯誤 CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 61646462eeba4918a4993b23f7f4b394083296ce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195886"
---
# <a name="expression-evaluator-error-cxx0019"></a>運算式評估工具錯誤 CXX0019

不正確的類型轉換

C 運算式評估工具無法執行已寫入的類型轉換。

此錯誤與 CAN0019 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 指定的類型不明。

1. 指標類型的層級太多。 例如，類型轉換

    ```
    (char **)h_message
    ```

   C 運算式評估工具無法評估。
