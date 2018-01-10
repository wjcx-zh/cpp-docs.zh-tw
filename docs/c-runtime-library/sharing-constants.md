---
title: "共用常數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
dev_langs: C++
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 635c6eee50f5d1dfb19f0c1b823dab018922c490
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="sharing-constants"></a>共用常數
檔案共用模式的常數。  
  
## <a name="syntax"></a>語法  
  
```  
  
#include <share.h>  
  
```  
  
## <a name="remarks"></a>備註  
 *shflag* 引數會決定共用模式，其中包含一或多個資訊清單常數。 這些可以和 *oflag* 引數結合 (請參閱[檔案常數](../c-runtime-library/file-constants.md))。  
  
 下表列出常數及其代表的意思：  
  
|常數|意義|  
|--------------|-------------|  
|`_SH_DENYRW`|拒絕對檔案的讀取和寫入存取|  
|`_SH_DENYWR`|拒絕對檔案的寫入存取|  
|`_SH_DENYRD`|拒絕對檔案的讀取存取|  
|`_SH_DENYNO`|允許讀取和寫入存取|  
|`_SH_SECURE`|設定安全模式 (共用讀取、獨佔寫入存取)。|  
  
## <a name="see-also"></a>請參閱  
 [_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [全域常數](../c-runtime-library/global-constants.md)