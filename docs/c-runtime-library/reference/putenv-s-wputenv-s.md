---
title: _putenv_s、_wputenv_s
ms.date: 4/2/2020
api_name:
- _wputenv_s
- _putenv_s
- _o__putenv_s
- _o__wputenv_s
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
ms.openlocfilehash: f0164feed05b409ba29ca713f11f4f3323dbaac3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338395"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s、_wputenv_s

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

*瓦爾名稱*<br/>
環境變數名稱。

*value_string*<br/>
要設定的環境變數值。

## <a name="return-value"></a>傳回值

如果成功則為 0，否則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*瓦爾名稱*|*value_string*|傳回值|
|------------|-------------|------------------|
|**空**|任意|**埃因瓦爾**|
|任意|**空**|**埃因瓦爾**|

如果發生其中一種錯誤狀況，這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,這些函數將傳回**EINVAL**並將**errno**設定為**EINVAL**。

## <a name="remarks"></a>備註

**_putenv_s**函數添加新的環境變數或修改現有環境變數的值。 環境變數會定義處理序所執行的環境 (例如，要與程式連結之程式庫的預設搜尋路徑)。 **_wputenv_s**是 **_putenv_s**的寬字元版本;**_wputenv_s的***串帶*參數是寬字元字串。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname*是要添加或修改的環境變數的名稱 *,value_string*是變數的值。 如果*varname*已經是環境的一部分,則其值將被*value_string*替換。否則,新的*varname*變數及其*value_string*將添加到環境中。 可以通過為*value_string*指定一個空字串(即"")從環境中刪除變數。

**_putenv_s**和 **_wputenv_s**僅影響當前流程的本地環境;不能使用它們來修改命令級環境。 這些函式只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為某個處理序所建立的環境「區段」上運作。 目前處理序終止時，環境會還原為呼叫處理序層級，而這在大部分情況下是作業系統層級。 但是,修改後的環境可以傳遞給**由_spawn、_exec**或**系統**創建的任何新進程,**_exec**這些新進程獲取由 **_putenv_s**和 **_wputenv_s**添加的任何新專案。

不要直接更改環境條目;而是使用 **_putenv_s**或 **_wputenv_s**來更改它。 特別是,直接釋放 **_environ_** 全域陣列的元素可能會導致處理無效的記憶體。

**getenv**和 **_putenv_s**使用全域變數 **_environ**訪問環境表;**_wgetenv**和 **_wputenv_s**使用 **_wenviron。** **_putenv_s**和 **_wputenv_s**可能會改變 **_environ**和 **_wenviron**的值,從而使*envp*參數無效為**主**參數 **,_wenvp****參數無效。** 因此,使用 **_environ**或 **_wenviron**訪問環境資訊更安全。 有關 **_putenv_s**與全域變數 **_wputenv_s**關係的詳細資訊,請參閱[_environ,_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **函數的_putenv_s**和 **_getenv_s**系列不具有線程安全性。 **_getenv_s**可以在 **_putenv_s**修改字串時返回字串指標,從而導致隨機失敗。 確定這些函式的呼叫已同步。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

有關演示如何使用 **_putenv_s**的範例,請參閱[getenv_s,_wgetenv_s](getenv-s-wgetenv-s.md)。

## <a name="see-also"></a>另請參閱

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、_wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
