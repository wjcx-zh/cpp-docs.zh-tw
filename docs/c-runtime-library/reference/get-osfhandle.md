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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 085bf20a12d9b77be0977521bde2ab75d9b2636a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918289"
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
> 當**stdin**、 **stdout**和**stderr**未與資料流程相關聯（例如，在沒有主控台視窗的 Windows 應用程式中）時，這些資料流程的檔案描述項值會從[_fileno](fileno.md)傳回為特殊值-2。 同樣地，如果您使用0、1或2做為檔案描述元參數，而不是呼叫 **_fileno**的結果，則當檔案描述項未與資料流程相關聯，且未設定**errno**時， **_get_osfhandle**也會傳回特殊值-2。 不過，這不是有效的檔案控制代碼值，而後續嘗試使用它的呼叫可能會失敗。

如需**EBADF**和其他錯誤碼的詳細資訊，請參閱[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

若要關閉 **_get_osfhandle**取得其作業系統（OS）檔案控制代碼的檔案，請在檔案描述器*fd*上呼叫[_close](close.md) 。 絕對不要在此函數的傳回值上呼叫**CloseHandle** 。 基礎作業系統檔案控制代碼是由*fd*檔案描述項所擁有，當在*fd*上呼叫[_close](close.md)時，會關閉。 如果檔案描述元是由`FILE *`資料流程所擁有，則在該`FILE *`資料流程上呼叫[fclose](fclose-fcloseall.md)會關閉檔案描述項和基礎作業系統檔案控制代碼。 在此情況下，請勿在檔案描述項上呼叫[_close](close.md) 。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup，_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
