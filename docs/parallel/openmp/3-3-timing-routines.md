---
title: 3.3 計時常式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21060d64-cbe8-4e38-8718-3a68d6a57be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3b8fc16e34124419362d5989131c2cf66df30b6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694907"
---
# <a name="33-timing-routines"></a>3.3 計時常式
本節中所述的函式支援可攜式時鐘計時器：  
  
-   `omp_get_wtime`函式會傳回耗用的時鐘時間。  
  
-   `omp_get_wtick`函式會傳回後續時鐘刻度之間的秒數。