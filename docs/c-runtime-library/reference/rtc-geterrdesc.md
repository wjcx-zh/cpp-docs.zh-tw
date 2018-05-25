---
title: _RTC_GetErrDesc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _RTC_GetErrDesc
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
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7154f6de192ee6b681ed0419126f3d4b682abb8c
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="rtcgeterrdesc"></a>_RTC_GetErrDesc

傳回執行階段錯誤檢查 (RTC) 類型的簡短描述。

## <a name="syntax"></a>語法

```C
const char * _RTC_GetErrDesc(
   _RTC_ErrorNumber errnum
);
```

### <a name="parameters"></a>參數

*errnum*<br/>
數字，介於零與 **_RTC_NumErrors** 所傳回的值減一之間。

## <a name="return-value"></a>傳回值

字元字串，包含一個執行階段錯誤檢查系統偵測到之錯誤類型之一的簡短描述。 若錯誤小於零或大於或等於所傳回的值[_RTC_NumErrors](rtc-numerrors.md)， **_RTC_GetErrDesc**傳回**NULL**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)<br/>
