---
title: 3.3.2 omp_get_wtick 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1ad08500-bcb0-40d9-a81f-f131819006c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0111e7ee1d4eba0a7ca9edf50d99cef8d052f6a1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380306"
---
# <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick 函式

`omp_get_wtick`函式會傳回雙精度浮點數值的秒數為後續的時鐘刻度之間。 格式如下：

```
#include <omp.h>
double omp_get_wtick(void);
```