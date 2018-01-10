---
title: "_WAIT_CHILD、_WAIT_GRANDCHILD | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs: C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1ac83e22e906a4e885860ec2254b2b732e31d38a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD、_WAIT_GRANDCHILD
## <a name="syntax"></a>語法  
  
```  
  
#include <process.h>  
  
```  
  
## <a name="remarks"></a>備註  
 `_cwait` 函式可以由任何處理序用來等候任何其他處理序 (若處理序識別碼為已知)。 動作引數可以是下列其中一個值：  
  
|常數|意義|  
|--------------|-------------|  
|`_WAIT_CHILD`|發出呼叫的處理序將等候指定的新處理序終止。|  
|`_WAIT_GRANDCHILD`|發出呼叫的處理序將等候指定的新處理序以及由該新處理序建立的所有處理序終止。|  
  
## <a name="see-also"></a>請參閱  
 [_cwait](../c-runtime-library/reference/cwait.md)   
 [全域常數](../c-runtime-library/global-constants.md)