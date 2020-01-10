---
title: _putenv_s、_wputenv_s
ms.date: 11/04/2016
api_name:
- _wputenv_s
- _putenv_s
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
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
ms.openlocfilehash: b2de609314a12f626a21680b470bc8831eada2cb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949895"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s、_wputenv_s

建立、修改或移除環境變數。 這些是 [_putenv、_wputenv](putenv-wputenv.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t _putenv_s(
   const char *varname,
   const char *value_string
);
errno_t _wputenv_s(
   const wchar_t *varname,
   const wchar_t *value_string
);
```

### <a name="parameters"></a>參數

*varname*<br/>
環境變數名稱。

*value_string*<br/>
要設定的環境變數值。

## <a name="return-value"></a>傳回值

如果成功則為 0，否則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*varname*|*value_string*|傳回值|
|------------|-------------|------------------|
|**NULL**|any|**EINVAL**|
|any|**NULL**|**EINVAL**|

如果發生其中一種錯誤狀況，這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回**EINVAL** ，並將**Errno**設定為**EINVAL**。

## <a name="remarks"></a>備註

**_Putenv_s**函數會加入新的環境變數，或修改現有環境變數的值。 環境變數會定義處理序所執行的環境 (例如，要與程式連結之程式庫的預設搜尋路徑)。 **_wputenv_s**是寬字元版本的 **_putenv_s**; **_wputenv_s**的*envstring*引數是寬字元字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname*是要加入或修改之環境變數的名稱，而*value_string*是變數的值。 如果*varname*已是環境的一部分，則其值會取代為*value_string*;否則，新的*varname*變數及其*value_string*會新增至環境。 您可以藉由指定*value_string*的空字串（也就是 ""），從環境中移除變數。

**_putenv_s**和 **_wputenv_s**只會影響目前進程的本機環境;您無法使用它們來修改命令層級的環境。 這些函式只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為某個處理序所建立的環境「區段」上運作。 目前處理序終止時，環境會還原為呼叫處理序層級，而這在大部分情況下是作業系統層級。 不過，修改過的環境可以傳遞至 **_spawn**、 **_exec**或**system**所建立的任何新進程，而這些新的進程會取得 **_putenv_s**和 **_wputenv_s**所新增的任何新專案。

請勿直接變更環境專案;相反地，請使用 **_putenv_s**或 **_wputenv_s**來變更它。 特別的是，直接釋放 **_environ []** 全域陣列的元素可能會導致無法處理的記憶體無效。

**getenv**和 **_putenv_s**會使用全域變數 **_environ**來存取環境資料表; **_wgetenv**和 **_wputenv_s**會使用 **_wenviron**。 **_putenv_s**和 **_wputenv_s**可能會變更 **_environ**和 **_wenviron**的值，因而使*envp*引數對**main**和 **_wenvp 引數**無效。 因此，使用 **_environ**或 **_wenviron**來存取環境資訊比較安全。 如需 **_putenv_s**和 **_wputenv_s**與全域變數之關聯性的詳細資訊，請參閱[_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> 函數的 **_putenv_s**和 **_getenv_s**系列不是安全線程。 當 **_putenv_s**正在修改字串時， **_getenv_s**可能會傳回字串指標，因而導致隨機失敗。 確定這些函式的呼叫已同步。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需顯示如何使用 **_putenv_s**的範例，請參閱[getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
