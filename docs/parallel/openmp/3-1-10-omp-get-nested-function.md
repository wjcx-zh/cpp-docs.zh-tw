---
title: "3.1.10 omp_get_nested 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36b213ee45018e7cc0ccf3a1cb99dcbd640d4457
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 函式
`omp_get_nested`函式會傳回非零值，如果已啟用巢狀平行處理原則和 0 已停用。 如需有關巢狀平行處理原則的詳細資訊，請參閱節 3.1.9 在 40 頁面上。 格式如下：  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 如果實作沒有實作巢狀平行處理原則，此函式一律傳回 0。