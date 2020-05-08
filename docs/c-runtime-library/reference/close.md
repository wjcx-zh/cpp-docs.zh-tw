---
title: _close
ms.date: 4/2/2020
api_name:
- _close
- _o__close
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
- _close
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: c642820bf1bc2e2afbd14e17832fb3fdb6f865b8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919846"
---
# <a name="_close"></a>_close

關閉檔案。

## <a name="syntax"></a>語法

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>參數

*fd*<br/>
參照已開啟之檔案的檔案描述元。

## <a name="return-value"></a>傳回值

如果成功關閉檔案， **_close**會傳回0。 傳回值-1 表示發生錯誤。

## <a name="remarks"></a>備註

**_Close**函式會關閉與*fd*相關聯的檔案。

關閉檔案描述元和基礎 OS 檔案控制代碼。 因此，如果檔案原本是使用 Win32 函式**CreateFile**開啟，並使用 **_open_osfhandle**轉換成檔案描述項，就不需要呼叫**CloseHandle** 。

這個函式會驗證它的參數。 如果*fd*是不正確的檔案描述項，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回-1，而**errno**會設定為**EBADF**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_open](open-wopen.md) 的範例。

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup，_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_unlink、_wunlink](unlink-wunlink.md)<br/>
