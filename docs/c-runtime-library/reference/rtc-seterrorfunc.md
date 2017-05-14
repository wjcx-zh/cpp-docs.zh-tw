---
title: _RTC_SetErrorFunc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _RTC_SetErrorFunc
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
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
dev_langs:
- C++
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: f5846074abafcbbb3cfe55cca00b9912dd0a994e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="rtcseterrorfunc"></a>_RTC_SetErrorFunc
指定函式做為報告執行階段錯誤檢查 (RTC) 的處理常式。 此函數已被取代。請改用 `_RTC_SetErrorFuncW` 。  
  
## <a name="syntax"></a>語法  
  
```  
  
      _RTC_error_fn _RTC_SetErrorFunc(  
   _RTC_error_fn function   
);  
```  
  
#### <a name="parameters"></a>參數  
 *function*  
 函式的位址，會處理執行階段錯誤檢查。  
  
## <a name="return-value"></a>傳回值  
 先前所定義的錯誤函式。 若先前未曾定義函式，會傳回 NULL。  
  
## <a name="remarks"></a>備註  
 請勿使用此函式。請改用 `_RTC_SetErrorFuncW`。 保留此函式的目的只在提供回溯相容性。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_RTC_SetErrorFunc`|\<rtcapi.h>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [_CrtDbgReport、_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)
