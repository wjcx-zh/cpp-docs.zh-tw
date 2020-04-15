---
title: _putenv、_wputenv
ms.date: 4/2/2020
api_name:
- _putenv
- _wputenv
- _o__putenv
- _o__wputenv
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 3e74959e6c6cdb2e27ce0d68ba40d02d64949904
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333034"
---
# <a name="_putenv-_wputenv"></a>_putenv、_wputenv

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

如果成功,則返回 0,如果出現錯誤,則返回 -1。

## <a name="remarks"></a>備註

**_putenv**函數添加新的環境變數或修改現有環境變數的值。 環境變數會定義處理序所執行的環境 (例如，要與程式連結之程式庫的預設搜尋路徑)。 **_wputenv**是 **_putenv**的寬字元版本;_wputenv*的串帶*參數 **_wputenv**是寬字元字串。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*envstring*參數必須是指向 value_string 形式*varname*=字串的*指標,其中* *varname*是要添加或修改的環境變數的名稱 *,value_string*是變數的值。 如果*varname*已經是環境的一部分,則其值將被*value_string*替換。否則,新的*varname*變數及其*value_string*值將添加到環境中。 可以通過指定空*value_string*從環境中刪除變數,或者換句話說,通過僅指定*varname**來從環境中刪除變數。

**_putenv**和 **_wputenv**僅影響當前流程的本地環境;不能使用它們來修改命令級環境。 換句話說，這些函式只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為某個處理序所建立的環境區段上運作。 目前處理序終止時，環境會還原為呼叫處理序層級 (在大部分情況下是作業系統層級)。 但是,修改後的環境可以傳遞給**由_spawn、_exec**或**系統**創建 **_exec**的任何新流程 ,這些新流程會獲得 **_putenv**和 **_wputenv**添加的任何新專案。

不要直接更改環境條目:而是使用 **_putenv**或 **_wputenv**來更改它。 特別是,**直接釋放_environ_** 全域陣列的元素可能會導致處理無效的記憶體。

**getenv**和 **_putenv**使用全域變數 **_environ**訪問環境表;**_wgetenv**和 **_wputenv**使用 **_wenviron。** **_putenv**和 **_wputenv**可能會改變 **_environ**和 **_wenviron**的值,從而使 **_envp**參數無效為**主**參數 **,_wenvp****參數無效。** 因此,使用 **_environ**或 **_wenviron**訪問環境資訊更安全。 有關 **_putenv**和 **_wputenv**與全域變數的關係的詳細資訊,請參閱[_environ,_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **函數的_putenv**和 **_getenv**系列不具有線程安全。 **_getenv**可以在 **_putenv**修改字串時返回字串指標,從而導致隨機失敗。 確定這些函式的呼叫已同步。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

有關如何使用 **_putenv**的範例,請參閱[getenv,_wgetenv](getenv-wgetenv.md)。

## <a name="see-also"></a>另請參閱

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
