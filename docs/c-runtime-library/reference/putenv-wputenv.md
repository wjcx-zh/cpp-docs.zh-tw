---
title: _putenv、_wputenv
ms.date: 11/04/2016
apiname:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 952a4d62f6ceb6b689091ac09f6ca338d0b10864
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357882"
---
# <a name="putenv-wputenv"></a>_putenv、_wputenv

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

傳回 0，如果成功或-1，如果發生錯誤。

## <a name="remarks"></a>備註

**_Putenv**函式加入新的環境變數，或修改現有的環境變數的值。 環境變數會定義處理序所執行的環境 (例如，要與程式連結之程式庫的預設搜尋路徑)。 **_wputenv**是寬字元版本的 **_putenv**; *envstring*引數 **_wputenv**是寬字元字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring*引數必須是格式的字串指標*varname*=*value_string*，其中*varname*是要加入或修改環境變數的名稱和*value_string*是變數的值。 如果*varname*已經環境的一部分，其值會取代*value_string*; 否則新*varname*變數並將其*value_string*值新增至環境。 您可以從環境移除變數，指定空*value_string*，或換句話說，是藉由只指定*varname*=。

**_putenv**並 **_wputenv**會影響目前的處理序的本機環境，您無法使用它們來修改命令層級環境。 換句話說，這些函式只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為某個處理序所建立的環境區段上運作。 目前處理序終止時，環境會還原為呼叫處理序層級 (在大部分情況下是作業系統層級)。 不過，修改過的環境可以傳遞至所建立的任何新處理序 **_spawn**， **_exec**，或**系統**，以及這些新的處理序會取得由加入任何新項目 **_putenv**並 **_wputenv**。

請勿直接變更環境項目： 請改用 **_putenv**或是 **_wputenv**加以變更。 特別是，直接釋出的項目 **_environ []** 全域陣列可能會導致無法處理的無效記憶體。

**getenv**並 **_putenv**使用全域變數 **_environ**存取環境資料表;**_wgetenv**並 **_wputenv**使用 **_wenviron**。 **_putenv**並 **_wputenv**可能會變更的值 **_environ**並 **_wenviron**，因此失效 **_envp**引數**主要**並 **_wenvp**引數**wmain**。 因此，它是安全的作法是使用 **_environ**或是 **_wenviron**存取環境資訊。 如需有關關聯性 **_putenv**並 **_wputenv**全域變數，請參閱[_environ、 _wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_Putenv**並 **_getenv**系列的函式不是安全執行緒。 **_getenv**可能會傳回字串指標，同時 **_putenv**正在修改字串，因而導致隨機失敗。 確定這些函式的呼叫已同步。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需如何使用的範例 **_putenv**，請參閱[getenv、 _wgetenv](getenv-wgetenv.md)。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
