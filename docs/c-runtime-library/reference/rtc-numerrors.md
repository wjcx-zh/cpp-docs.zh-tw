---
title: _RTC_NumErrors
ms.date: 11/04/2016
apiname:
- _RTC_NumErrors
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
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
ms.openlocfilehash: c5e79f388164670e0fa48438d68a9b35d29f812d
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524959"
---
# <a name="rtcnumerrors"></a>_RTC_NumErrors

傳回執行階段錯誤檢查 (RTC) 可以偵測到的錯誤數總計。 您可以使用此數字作為 **for** 迴圈的控制項。在此迴圈中，每個值都會傳遞給 [_RTC_GetErrDesc](rtc-geterrdesc.md)。

## <a name="syntax"></a>語法

```C

int _RTC_NumErrors( void );
```

## <a name="return-value"></a>傳回值

整數，其值代表 Visual C++ 執行階段錯誤檢查可以偵測到的錯誤數總計。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_RTC_NumErrors**|\<rtcapi.h>|

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)<br/>
