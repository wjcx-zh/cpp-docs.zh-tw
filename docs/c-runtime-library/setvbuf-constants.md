---
title: "setvbuf 常數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
dev_langs:
- C++
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 72597020534100f86de855db0095995e50d10f9b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="setvbuf-constants"></a>setvbuf 常數
## <a name="syntax"></a>語法  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>備註  
 這些常數表示 `setvbuf` 的緩衝區類型。  
  
 下列資訊清單常數會提供可能的值：  
  
|常數|意義|  
|--------------|-------------|  
|`_IOFBF`|完整緩衝：會使用在 `setvbuf` 呼叫中所指定的緩衝區，且其大小會和 `setvbuf` 呼叫中所指定的大小相同。 如果緩衝區指標為 **NULL**，則會使用指定大小的自動配置緩衝區。|  
|`_IOLBF`|與 `_IOFBF` 相同。|  
|`_IONBF`|不使用緩衝區，不論 `setvbuf` 呼叫中的引數為何。|  
  
## <a name="see-also"></a>另請參閱  
 [setbuf](../c-runtime-library/reference/setbuf.md)   
 [全域常數](../c-runtime-library/global-constants.md)
