---
title: 2.6.1 master 建構
ms.date: 11/04/2016
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
ms.openlocfilehash: 0501b1fdfbd36829cee2793fc0f7bb03daeda900
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475526"
---
# <a name="261-master-construct"></a>2.6.1 master 建構

**主要**指示詞會識別指定小組的主要執行緒所執行的結構化的區塊的建構。 語法**主要**指示詞時，如下所示：

```
#pragma omp master new-linestructured-block
```

在小組中的其他執行緒不會執行相關聯的結構化的區塊。 沒有任何隱含的障礙，項目，或從 master 建構結束。