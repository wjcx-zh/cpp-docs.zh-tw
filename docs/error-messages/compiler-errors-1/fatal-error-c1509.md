---
title: 嚴重錯誤 C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: efd5b9dd5cdd7ee174bc786c38d9dd841e2ad6ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619998"
---
# <a name="fatal-error-c1509"></a>嚴重錯誤 C1509

編譯器限制： 函式 'function' 中的例外狀況處理常式狀態太多。 請簡化函式

程式碼超過例外狀況處理常式狀態 （32,768 狀態） 的內部限制。

最常見的原因是函式包含使用者定義的類別變數及算術運算子的複雜運算式。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 將通用子運算式指派給暫存變數，以簡化的運算式。

1. 將函式分割成較小的函式。