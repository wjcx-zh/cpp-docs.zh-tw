---
title: _RTC_NumErrors | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_NumErrors
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
- _RTC_NumErrors
- RTC_NumErrors
dev_langs: C++
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 62e734fb1165bf0d4e59f3d964a20056fa7065f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="rtcnumerrors"></a>_RTC_NumErrors
傳回執行階段錯誤檢查 (RTC) 可以偵測到的錯誤數總計。 您可以使用此數字作為 **for** 迴圈的控制項。在此迴圈中，每個值都會傳遞給 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
int _RTC_NumErrors( void );  
  
```  
  
## <a name="return-value"></a>傳回值  
 整數，其值代表 Visual C++ 執行階段錯誤檢查可以偵測到的錯誤數總計。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_RTC_NumErrors`|\<rtcapi.h>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)