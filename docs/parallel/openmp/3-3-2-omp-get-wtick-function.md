---
title: 3.3.2 omp_get_wtick 函式 |Microsoft 文件
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
ms.openlocfilehash: 9119a2226fc67058f8d1848b45e6902bae0b361c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688709"
---
# <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick 函式
`omp_get_wtick`函式會傳回雙精確度浮點值的秒數等於後續時鐘刻度之間。 格式如下：  
  
```  
#include <omp.h>  
double omp_get_wtick(void);  
```