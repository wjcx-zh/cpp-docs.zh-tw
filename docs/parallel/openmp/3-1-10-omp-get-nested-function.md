---
title: 3.1.10 omp_get_nested 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d019dd757080bbc87ff7aaab1a8745b2a3156b39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392277"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 函式

`omp_get_nested`函式會傳回非零值，如果巢狀平行處理原則已啟用而 0 會停用。 如需有關巢狀平行處理原則的詳細資訊，請參閱節 3.1.9 在 40 頁面上。 格式如下：

```
#include <omp.h>
int omp_get_nested(void);
```

如果實作不會實作巢狀平行處理原則，則此函式一律會傳回 0。