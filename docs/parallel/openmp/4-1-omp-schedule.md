---
title: 4.1 OMP_SCHEDULE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cbdad5ab56ea6979ae2b5952b092b5e85c7bdfa8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433448"
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

**OMP_SCHEDULE**僅適用於**for**並**平行的**有排程類型的指示詞**執行階段**。 所有這類迴圈的排程類型與區塊大小可在執行階段設定，藉由設定這個環境變數，任何可辨識的排程類型，並選擇性*chunk_size*。

針對**針對**和**的平行**以外的其他已排程類型的指示詞**執行階段**， **OMP_SCHEDULE**會被忽略。 這個環境變數的預設值是由實作定義。 如果選擇性*chunk_size*設定，此值必須是正數。 如果*chunk_size*未設定，會假設值為 1，例外的情況**靜態**排程。 針對**靜態**排程，預設區塊大小設定為迴圈的反覆項目空間除以套用到迴圈的執行緒數目。

範例：

```
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

## <a name="cross-references"></a>交叉參考：

- **針對**指示詞，請參閱[一節 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁上。

- **針對平行**指示詞，請參閱[一節 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md)在 16 頁面上。