---
title: 運算式評估工具錯誤 CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: 64ebce0161d67c298d55095f6bc409820120c34a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196010"
---
# <a name="expression-evaluator-error-cxx0017"></a>運算式評估工具錯誤 CXX0017

找不到符號

找不到在運算式中指定的符號。

這個錯誤的其中一個可能原因是符號名稱中的大小寫不相符。 因為 C 和C++都是區分大小寫的語言，所以必須在來源中定義的確切大小寫中指定符號名稱。

嘗試轉換變數以在進行調試過程中監看變數時，可能會發生此錯誤。 `typedef` 會宣告類型的新名稱，但不會定義新的類型。 在偵錯工具中嘗試的轉換需要已定義類型的名稱。

此錯誤與 CAN0017 相同。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 請確定已在程式中使用該符號的那一點宣告該符號。

1. 使用實際的型別名稱來轉換偵錯工具中的變數，而不是 `typedef`定義的名稱。
