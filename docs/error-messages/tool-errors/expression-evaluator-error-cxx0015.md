---
title: 運算式評估工具錯誤 CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: 19cf47d6b7b718eb19b987bcc16854af3266069b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196062"
---
# <a name="expression-evaluator-error-cxx0015"></a>運算式評估工具錯誤 CXX0015

運算式太複雜（堆疊溢位）

輸入的運算式太複雜或太深，無法用於 C 運算式評估工具的儲存空間數量。

溢位通常是因為太多暫止的計算所造成。

重新排列運算式，讓運算式的每個元件都可以在遇到時進行評估，而不必等候計算運算式的其他部分。

將運算式分成多個命令。

此錯誤與 CAN0015 相同。
