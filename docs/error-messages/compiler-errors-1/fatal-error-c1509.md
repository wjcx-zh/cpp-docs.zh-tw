---
title: 嚴重錯誤 C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: 0d1d7255dd64239a6a76bb15a1f309b43eac0d4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202952"
---
# <a name="fatal-error-c1509"></a>嚴重錯誤 C1509

編譯器限制：函式 ' function ' 中有太多例外狀況處理常式狀態。 簡化函數

程式碼超過例外狀況處理常式狀態的內部限制（32768狀態）。

最常見的原因是函數包含使用者定義之類別變數和算術運算子的複雜運算式。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 藉由將通用子運算式指派給暫存變數來簡化運算式。

1. 將函數分割成較小的函式。
