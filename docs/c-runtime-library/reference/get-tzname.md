---
title: _get_tzname | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_tzname
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_tzname
- get_tzname
dev_langs: C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f70e928c3877bf5d660231cbe2646f6cf72575e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="gettzname"></a>_get_tzname
擷取代表時區名稱或日光節約標準時區名稱 (DST) 的字元字串。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _get_tzname(  
    size_t* pReturnValue,  
    char* timeZoneName,  
    size_t sizeInBytes,  
    int index      
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `pReturnValue`  
 `timeZoneName` 的字串長度包括 Null 結束字元。  
  
 [輸出] `timeZoneName`  
 代表時區名稱或日光節約標準時區名稱 (DST) 的字元字串的位址，取決於 `index`。  
  
 [輸入] `sizeInBytes`  
 `timeZoneName` 字元字串的大小，以位元組為單位。  
  
 [輸入] `index`  
 要擷取的兩個時區名稱中，其中一個時區名稱的索引。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為零，否則為 `errno` 類型的值。  
  
 如果 `timeZoneName` 為 `NULL`，或 `sizeInBytes` 為零或小於零 (但非兩者皆是)，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`pReturnValue`|`timeZoneName`|`sizeInBytes`|`index`|傳回值|`timeZoneName` 的內容。|  
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|  
|時區名稱的大小|`NULL`|0|0 或 1|0|未修改|  
|時區名稱的大小|any|> 0|0 或 1|0|時區名稱|  
|未修改|`NULL`|> 0|any|`EINVAL`|未修改|  
|未修改|any|零|any|`EINVAL`|未修改|  
|未修改|any|> 0|> 1|`EINVAL`|未修改|  
  
## <a name="remarks"></a>備註  
 `_get_tzname` 函式會擷取代表時區名稱或日光節約標準時區名稱 (DST) 的字元字串，依據索引值放入 `timeZoneName` 位址，以及 `pReturnValue`。 如果 `timeZoneName` 是 `NULL`，且 `sizeInBytes` 為零，則 `pReturnValue` 只會傳回其中一個時區的字串大小，以位元組為單位。 標準時區的索引值必須為 0 或日光節約標準時區的索引值必須為 1；任何索引的其他值均為未定結果。  
  
### <a name="index-values"></a>索引值  
  
|`index`|`timeZoneName` 的內容。|`timeZoneName` 預設值|  
|-------------|--------------------------------|----------------------------------|  
|0|時區名稱|"PST"|  
|1|日光節約標準時區名稱|"PDT"|  
|> 1 或 < 0|請將 `errno` 設為 `EINVAL`|未修改|  
  
 除非在執行階段期間明確地變更值，否則預設值分別為 "PST" 和 "PDT"。  這些字元陣列的大小都受到 `TZNAME_MAX` 值的規範。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_get_tzname`|\<time.h>|  
  
 如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [errno、_doserrno、_sys_errlist 和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [_get_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [TZNAME_MAX](../../c-runtime-library/tzname-max.md)