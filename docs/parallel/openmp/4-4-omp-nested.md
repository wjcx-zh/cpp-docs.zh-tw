---
title: 4.4 OMP_NESTED |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1083269f31ebc710da24430635ff8381e3f2147a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419512"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED`環境變數啟用或停用巢狀平行處理原則，除非巢狀平行處理原則已啟用或停用藉由呼叫`o` **mp_set_nested**程式庫常式。 如果設定為 **，則為 TRUE**，啟用巢狀平行處理原則; 如果設為**FALSE**巢狀平行處理原則已停用。 預設值是**FALSE**。

範例：

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>交叉參考：

- `omp_set_nested` 函式，請參閱 <<c0> [ 一節 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上。