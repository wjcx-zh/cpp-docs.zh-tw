---
title: 執行階段錯誤檢查
ms.date: 11/04/2016
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
ms.openlocfilehash: cf707cbd53e2285684d53d3f440db0f618343598
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444839"
---
# <a name="run-time-error-checking"></a>執行階段錯誤檢查

C 執行階段程式庫包含支援執行階段錯誤檢查 (RTC) 的函式。 執行階段錯誤檢查可讓您建置您的程式報告特定類型的執行階段錯誤。 您要指定報告錯誤的方式，以及報告哪些類型的錯誤。 如需詳細資訊，請參閱[如何：使用原生執行階段檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)。

使用下列函式來自訂您的程式執行執行階段錯誤檢查的方式。

## <a name="run-time-error-checking-functions"></a>執行階段錯誤檢查函式

|函式|使用|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|傳回執行階段錯誤檢查類型的簡短描述。|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|傳回執行階段錯誤檢查可以偵測到的錯誤數總計。|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|指定函式做為報告執行階段錯誤檢查的處理常式。|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|將執行階段錯誤檢查所偵測到的錯誤與類型建立關聯。|

## <a name="see-also"></a>另請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
[/RTC (執行階段錯誤檢查)](../build/reference/rtc-run-time-error-checks.md)<br/>
[runtime_checks](../preprocessor/runtime-checks.md)<br/>
[偵錯常式](../c-runtime-library/debug-routines.md)<br/>
