---
title: 運算式評估工具錯誤 CXX0017 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 431071137fb3f5b1b276327ee7d21f323ac24c5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136233"
---
# <a name="expression-evaluator-error-cxx0017"></a>運算式評估工具錯誤 CXX0017

找不到符號

找不到運算式中指定的符號。

此錯誤的其中一個可能的原因是符號名稱的大小寫不符。 因為 C 和 c + + 是區分大小寫的語言，就必須指定符號名稱中它定義在來源中的大小寫完全相符。

嘗試轉換變數類型在偵錯期間監看變數時，會發生此錯誤。 `typedef`宣告的新名稱的類型，但它不會定義新的類型。 試圖偵錯工具需要有已定義的類型名稱。

此錯誤是與 can0017 相同。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 請確定符號已宣告它的使用位置的程式中的點。

1. 使用實際的類型名稱來轉換變數在偵錯工具，而非`typedef`-定義的名稱。