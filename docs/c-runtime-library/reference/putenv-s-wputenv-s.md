---
title: _putenv_s、_wputenv_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wputenv_s
- _putenv_s
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
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
dev_langs:
- C++
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e84d7a68530a748c9b1ad7c553fad80ed4e7c86b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="putenvs-wputenvs"></a>_putenv_s、_wputenv_s

建立、修改或移除環境變數。 這些是 [_putenv、_wputenv](putenv-wputenv.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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
|**NULL**|任何|**EINVAL**|
|任何|**NULL**|**EINVAL**|

如果發生其中一種錯誤狀況，這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函數會傳回**EINVAL**並設定**errno**至**EINVAL**。

## <a name="remarks"></a>備註

**_Putenv_s**函式加入新的環境變數，或修改現有的環境變數的值。 環境變數會定義處理序所執行的環境 (例如，要與程式連結之程式庫的預設搜尋路徑)。 **_wputenv_s**是寬字元版本的 **_putenv_s**; *envstring*引數 **_wputenv_s**是寬字元字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname*是要加入或修改環境變數的名稱和*value_string*是變數的值。 如果*varname*已經屬於環境，其值會取代*value_string*; 否則新*varname*變數及其*value_string*新增至環境。 您可以從環境移除變數，藉由指定空字串 (也就是"") 為*value_string*。

**_putenv_s**和 **_wputenv_s**會影響目前的處理序的本機環境; 您無法使用它們來修改命令層級環境。 這些函式只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為某個處理序所建立的環境「區段」上運作。 目前處理序終止時，環境會還原為呼叫處理序層級，而這在大部分情況下是作業系統層級。 不過，修改過的環境可以傳遞至所建立的任何新處理序 **_spawn**， **_exec**，或**系統**，以及這些新的處理程序取得的任何新項目加入 **_putenv_s**和 **_wputenv_s**。

請勿直接; 變更環境項目請改用 **_putenv_s**或 **_wputenv_s**加以變更。 特別是，直接釋出的項目 **_environ []** 全域陣列可能會導致無效的記憶體來處理。

**getenv**和 **_putenv_s**使用全域變數 **_environ**存取環境資料表;**_wgetenv**和 **_wputenv_s**使用 **_wenviron**。 **_putenv_s**和 **_wputenv_s**可能的值變更 **_environ**和 **_wenviron**，藉此讓*envp*引數**主要**和 **_wenvp**引數**wmain**。 因此，它是安全的作法是使用 **_environ**或 **_wenviron**存取環境資訊。 如需有關與的關聯性 **_putenv_s**和 **_wputenv_s**全域變數，請參閱[_environ、 _wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_Putenv_s**和 **_getenv_s**系列的函式不是安全執行緒。 **_getenv_s**無法傳回字串的指標時 **_putenv_s**修改字串，並因而導致隨機失敗。 確定這些函式的呼叫已同步。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需範例，示範如何使用 **_putenv_s**，請參閱[getenv_s、 _wgetenv_s](getenv-s-wgetenv-s.md)。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
