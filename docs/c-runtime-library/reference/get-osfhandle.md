---
title: _get_osfhandle
ms.date: 05/29/2018
api_name:
- _get_osfhandle
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
ms.openlocfilehash: 65060689e0a7fc72b67da8fc3bf7ce0af75fd645
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955776"
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

*fd*<br/>
現有的檔案描述元。

## <a name="return-value"></a>傳回值

如果*fd*有效，會傳回作業系統檔案控制代碼。 否則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回**INVALID_HANDLE_VALUE** （-1）。 它也會將**errno**設定為**EBADF**，表示不正確檔案控制代碼。 若要避免在使用結果做為 Win32 檔案控制代碼時出現警告，請將它轉換成**控制碼**類型。

> [!NOTE]
> 當**stdin**、 **stdout**和**stderr**未與資料流程相關聯（例如，在沒有主控台視窗的 Windows 應用程式中）時，這些資料流程的檔案描述項值會從[_fileno](fileno.md)傳回為特殊值-2。 同樣地，如果您使用0、1或2做為檔案描述元參數，而不是呼叫 **_fileno**的結果，則 **_get_osfhandle**也會在檔案描述項未與資料流程相關聯，且未設定**errno**時，傳回特殊的值-2。 不過，這不是有效的檔案控制代碼值，而後續嘗試使用它的呼叫可能會失敗。

如需**EBADF**和其他錯誤碼的詳細資訊，請參閱[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

若要關閉由 **_get_osfhandle**取得其作業系統（OS）檔案控制代碼的檔案，請在檔案描述器*fd*上呼叫[_close](close.md) 。 絕對不要在此函數的傳回值上呼叫**CloseHandle** 。 基礎作業系統檔案控制代碼是由*fd*檔案描述項所擁有，並在*fd*上呼叫[_close](close.md)時關閉。 如果檔案描述元是由`FILE *`資料流程所擁有，則在該`FILE *`資料流程上呼叫[fclose](fclose-fcloseall.md)會關閉檔案描述項和基礎作業系統檔案控制代碼。 在此情況下，請不要在檔案描述項上呼叫[_close](close.md) 。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[dup、dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
