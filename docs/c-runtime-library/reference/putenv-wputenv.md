---
title: _putenv、_wputenv
ms.date: 11/04/2016
api_name:
- _putenv
- _wputenv
api_location:
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
ms.openlocfilehash: 8fe699a476ea1dd09a6ce9922294bce398df16b2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949887"
---
# <a name="_putenv-_wputenv"></a>_putenv、_wputenv

建立、修改或移除環境變數。 這些函式已有更安全的版本可用，請參閱 [_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _putenv(
   const char *envstring
);
int _wputenv(
   const wchar_t *envstring
);
```

### <a name="parameters"></a>參數

*envstring*<br/>
環境字串定義。

## <a name="return-value"></a>傳回值

如果成功，則傳回0，如果發生錯誤，則傳回-1。

## <a name="remarks"></a>備註

**_Putenv**函數會加入新的環境變數，或修改現有環境變數的值。 環境變數會定義處理序所執行的環境 (例如，要與程式連結之程式庫的預設搜尋路徑)。 **_wputenv**是寬字元版本的 **_putenv**; **_wputenv**的*envstring*引數是寬字元字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring*引數必須是*varname* = *value_string*格式之字串的指標，其中*varname*是要加入或修改之環境變數的名稱，而*value_string*是變數的value. 如果*varname*已是環境的一部分，則其值會取代為*value_string*;否則，新的*varname*變數及其*value_string*值會加入至環境。 您可以藉由指定空的*value_string*，或是只指定*varname*=，從環境中移除變數。

**_putenv**和 **_wputenv**只會影響目前進程的本機環境;您無法使用它們來修改命令層級的環境。 換句話說，這些函式只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為某個處理序所建立的環境區段上運作。 目前處理序終止時，環境會還原為呼叫處理序層級 (在大部分情況下是作業系統層級)。 不過，修改過的環境可以傳遞至 **_spawn**、 **_exec**或**system**所建立的任何新進程，而這些新的進程會取得 **_putenv**和 **_wputenv**所新增的任何新專案。

請不要直接變更環境專案：改為使用 **_putenv**或 **_wputenv**來加以變更。 特別的是， **_environ []** 全域陣列的直接釋放專案可能會導致定址的記憶體無效。

**getenv**和 **_putenv**會使用全域變數 **_environ**來存取環境資料表; **_wgetenv**和 **_wputenv**會使用 **_wenviron**。 **_putenv**和 **_wputenv**可能會變更 **_environ**和 **_wenviron**的值，因而使 **_envp**引數對**main**和 _wenvp**引數**失效 **。** 因此，使用 **_environ**或 **_wenviron**來存取環境資訊比較安全。 如需 **_putenv**和 **_wputenv**與全域變數之關聯的詳細資訊，請參閱[_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> 函數的 **_putenv**和 **_getenv**系列不是安全線程。 當 **_putenv**正在修改字串時， **_getenv**可能會傳回字串指標，因而導致隨機失敗。 確定這些函式的呼叫已同步。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需如何使用 **_putenv**的範例，請參閱[getenv、_wgetenv](getenv-wgetenv.md)。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
