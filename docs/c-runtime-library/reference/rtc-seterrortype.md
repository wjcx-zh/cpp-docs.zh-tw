---
title: _RTC_SetErrorType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
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
ms.openlocfilehash: 78f056e65523a39477bf138e6bd1664e0945a899
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType
關聯的執行階段錯誤檢查 (RTC) 所偵測到的錯誤與類型。 錯誤處理常式會處理如何輸出指定類型的錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
  
      int _RTC_SetErrorType(  
   _RTC_ErrorNumber errnum,  
   int ErrType   
);  
```  
  
#### <a name="parameters"></a>參數  
 *errnum*  
 數字，介於 0 與 [_RTC_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md)傳回的值之間。  
  
 *ErrType*  
 值，會指派給此 *errnum*。 例如，您可以使用 **_CRT_ERROR**。 若是使用 `_CrtDbgReport` 做為您的錯誤處理常式， *ErrType* 可能會是 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md)中唯一定的符號。 若您有自己的錯誤處理常式 ([_RTC_SetErrorFunc](../../c-runtime-library/reference/rtc-seterrorfunc.md))，您可以有可以有和 *errnum*等量的 *ErrType*。  
  
 _RTC_ERRTYPE_IGNORE 的 *ErrType* 對 `_CrtSetReportMode`而言有特殊意義；此錯誤會予忽略。  
  
## <a name="return-value"></a>傳回值  
 錯誤類型 `type`先前的值。  
  
## <a name="remarks"></a>備註  
 所有錯誤的預設設定皆為 *ErrType* = 1，與 **_CRT_ERROR**相對應。 如需預設錯誤類型 (例如 **_CRT_ERROR**) 的詳細資訊，請參閱 [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)。  
  
 您必須先呼叫任一個執行階段錯誤檢查初始化函式，才能呼叫此函式。請參閱[不使用 C 語言執行階段程式庫進行執行階段檢查](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_RTC_SetErrorType`|\<rtcapi.h>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)
