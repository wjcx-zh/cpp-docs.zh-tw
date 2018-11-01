---
title: 2.6.2 critical 建構
ms.date: 11/04/2016
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
ms.openlocfilehash: dcc0e6144be5daee2a225cda621db818e5a38e2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539070"
---
# <a name="262-critical-construct"></a>2.6.2 critical 建構

**重要**指示詞會識別相關聯的結構化區塊執行的限制為單一執行緒，一次的建構。 語法**重要**指示詞時，如下所示：

```
#pragma omp critical [(name)]  new-linestructured-block
```

選擇性*名稱*可能用來識別重要區域。 用來識別重要區域的識別項具有外部連結，並會在命名空間是分開的標籤、 標記、 成員和一般識別項使用的命名空間中。

在關鍵區域的開頭的執行緒等候，直到沒有其他執行緒正在執行 （在程式中） 具有相同名稱的關鍵區域。 所有未命名**重要**指示詞對應至相同的未指定名稱。