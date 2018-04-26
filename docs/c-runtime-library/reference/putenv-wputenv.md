---
title: _putenv、_wputenv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74984106c94ec3b6af1811fba63707d7d5056791
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="putenv-wputenv"></a>_putenv、_wputenv

建立、修改或移除環境變數。 這些函式已有更安全的版本可用，請參閱 [_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

傳回 0，如果成功則為-1 在錯誤的情況下。

## <a name="remarks"></a>備註

**_Putenv**函式加入新的環境變數，或修改現有的環境變數的值。 環境變數會定義處理序所執行的環境 (例如，要與程式連結之程式庫的預設搜尋路徑)。 **_wputenv**是寬字元版本的 **_putenv**; *envstring*引數 **_wputenv**是寬字元字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring*引數必須是格式的字串指標*varname*=*value_string*，其中*varname*是若要加入或修改環境變數的名稱和*value_string*是變數的值。 如果*varname*已經屬於環境，其值會取代*value_string*; 否則新*varname*變數及其*value_string*值會加入至環境。 您可以從環境移除變數，藉由指定空白*value_string*，或換句話說，藉由只指定*varname*=。

**_putenv**和 **_wputenv**會影響目前的處理序的本機環境; 您無法使用它們來修改命令層級環境。 換句話說，這些函式只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為某個處理序所建立的環境區段上運作。 目前處理序終止時，環境會還原為呼叫處理序層級 (在大部分情況下是作業系統層級)。 不過，修改過的環境可以傳遞至所建立的任何新處理序 **_spawn**， **_exec**，或**系統**，與這些新的處理序會取得由加入任何新項目 **_putenv**和 **_wputenv**。

請勿直接變更環境項目： 請改用 **_putenv**或 **_wputenv**加以變更。 特別是，直接釋出的項目 **_environ []** 全域陣列可能會導致要定址的無效記憶體。

**getenv**和 **_putenv**使用全域變數 **_environ**存取環境資料表;**_wgetenv**和 **_wputenv**使用 **_wenviron**。 **_putenv**和 **_wputenv**可能的值變更 **_environ**和 **_wenviron**，因此失效 **_envp**引數**主要**和 **_wenvp**引數**wmain**。 因此，它是安全的作法是使用 **_environ**或 **_wenviron**存取環境資訊。 如需有關之關聯性 **_putenv**和 **_wputenv**全域變數，請參閱[_environ、 _wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_Putenv**和 **_getenv**系列的函式不是安全執行緒。 **_getenv**無法傳回字串的指標時 **_putenv**正在修改字串，會導致隨機失敗。 確定這些函式的呼叫已同步。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需使用方式的範例 **_putenv**，請參閱[getenv、 _wgetenv](getenv-wgetenv.md)。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
