---
title: 3.3.1 omp_get_wtime 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d71296d23df72464ed730713566c95e2403760a1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689489"
---
# <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime 函式
`omp_get_wtime`函式會傳回雙精確度浮點數值等於耗用的時鐘時間 （秒），因為某些 「 時間過去 」。  實際"過去的時間 」 是任意的但它保證不會在應用程式執行期間變更。 格式如下：  
  
```  
#include <omp.h>  
double omp_get_wtime(void);  
```  
  
 它會預期函式，可用來測量已耗用時間，如下列範例所示：  
  
```  
double start;  
double end;  
start = omp_get_wtime();  
... work to be timed ...  
end = omp_get_wtime();  
printf_s("Work took %f sec. time.\n", end-start);  
```  
  
 傳回的時間都不需要它們參與應用程式中的所有執行緒都是全域一致適 「 每個執行緒的時間 」。