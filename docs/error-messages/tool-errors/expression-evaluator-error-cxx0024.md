---
title: 運算式評估工具錯誤 CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 525210090b0a4c2966f2e1432f85fd4bb6a8156d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195756"
---
# <a name="expression-evaluator-error-cxx0024"></a>運算式評估工具錯誤 CXX0024

作業需要左值

針對需要左值的作業，指定了未評估為左值的運算式。

左值（因此呼叫，因為它出現在指派語句的左邊）是參考記憶體位置的運算式。

例如，`buffer[count]` 是有效的左值，因為它會指向特定的記憶體位置。 邏輯比較 `zed != 0` 不是有效的左值，因為它會評估為 TRUE 或 FALSE，而不是記憶體位址。

此錯誤與 CAN0024 相同。
