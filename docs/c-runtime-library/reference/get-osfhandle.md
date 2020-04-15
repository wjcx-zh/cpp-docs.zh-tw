---
title: _get_osfhandle
ms.date: 4/2/2020
api_name:
- _get_osfhandle
- _o__get_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: a12c0c93ae15350a4b91a8aa905acb941f8b6a10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345035"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

擷取與指定的檔案描述元相關聯的作業系統檔案控制代碼。

## <a name="syntax"></a>語法

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>參數

*Fd*<br/>
現有的檔案描述元。

## <a name="return-value"></a>傳回值

如果*fd*有效,則返回作業系統檔句柄。 否則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,它將返回**INVALID_HANDLE_VALUE** (-1)。 它還將**errno**設置到**EBADF,** 指示無效的檔句柄。 為避免將結果用作 Win32 檔句柄時出現警告,請將其轉換為**HANDLE**類型。

> [!NOTE]
> 當**stdin、stdout**和**stderr**不與流關聯時(例如,在沒有控制台視窗的 Windows 應用程式中),這些流的**stdout**檔描述符值將從[_fileno](fileno.md)返回為特殊值 -2。 同樣,如果使用 0、1 或 2 作為檔描述符參數而不是調用 **_fileno**的結果,則當檔描述符不與流關聯且不設置**errno**時 **,_get_osfhandle**也會返回特殊值 -2。 但是,這不是有效的檔句柄值,嘗試使用它的後續調用可能會失敗。

有關**EBADF**和其他錯誤代碼的詳細資訊,請參閱[_doserrno、errno、_sys_errlist和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

要關閉其作業系統 (OS) 檔片將 **_get_osfhandle**取得的檔案,請呼叫[_close](close.md)檔案描述*符 fd*。 切勿在此函數的返回值上調用**CloseHandle。** 基礎 OS 檔句柄由*fd*檔描述符擁有,並在*在 fd*上調用[_close](close.md)時關閉。 如果檔描述符由`FILE *`流擁有,則在`FILE *`該 流上調用[fclose](fclose-fcloseall.md)將關閉檔描述符和基礎 OS 檔句柄。 在這種情況下,不要在檔描述符上調用[_close。](close.md)

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup,_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
