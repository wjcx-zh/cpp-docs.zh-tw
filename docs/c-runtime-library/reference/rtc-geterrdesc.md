---
title: _RTC_GetErrDesc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_GetErrDesc
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
apitype: DLLExport
f1_keywords:
- RTC_GetErrDesc
- _RTC_GetErrDesc
dev_langs: C++
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3149c1be671566785f67963368a50cdf2eee3809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="rtcgeterrdesc"></a>_RTC_GetErrDesc
傳回執行階段錯誤檢查 (RTC) 類型的簡短描述。  
  
## <a name="syntax"></a>語法  
  
```  
  
      const char * _RTC_GetErrDesc(  
   _RTC_ErrorNumber errnum   
);  
```  
  
#### <a name="parameters"></a>參數  
 *errnum*  
 數字，介於 0 與小於 `_RTC_NumErrors`的值之間。  
  
## <a name="return-value"></a>傳回值  
 字元字串，包含一個執行階段錯誤檢查系統偵測到之錯誤類型之一的簡短描述。 如果錯誤小於零或大於或等於 [_RTC_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md) 所傳回的值，則 `_RTC_GetErrDesc` 會傳回 NULL。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_RTC_GetErrDesc`|\<rtcapi.h>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>請參閱  
 [_RTC_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md)   
 [執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)