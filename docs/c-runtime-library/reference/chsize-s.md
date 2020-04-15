---
title: _chsize_s
ms.date: 4/2/2020
api_name:
- _chsize_s
- _o__chsize_s
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
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: 70845124eb889d73a0f87aadd923e2d86db96c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350073"
---
# <a name="_chsize_s"></a>_chsize_s

變更檔案大小。 這是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_chsize](chsize.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>參數

*Fd*<br/>
參照已開啟之檔案的檔案描述元。

*大小*<br/>
檔案的新長度 (位元組)。

## <a name="return-value"></a>傳回值

如果檔大小已成功更改 **,_chsize_s**返回值 0。 非零返回值表示錯誤:如果指定檔針對訪問鎖定,則返回值為**EACCES;** 如果指定的檔為唯讀或描述符無效,則返回值為 EACCES;如果**設備上**沒有空間,則返回值為 EINVAL;如果大小小於零,則返回值為**EINVAL。** **EBADF** **errno**設置為相同的值。

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_chsize_s**函數將與*fd*關聯的檔延伸或截截到*大小*指定的長度。 檔案必須以允許寫入的模式開啟。 如果擴充檔案，則會附加 Null 字元 ('\0')。 如果檔案遭到截斷，則會遺失從縮短檔案結尾到檔案原始長度的所有資料。

**_chsize_s**以 64 位整數作為檔大小,因此可以處理大於 4 GB 的檔案大小。 **_chsize**限制為 32 位元檔大小。

這個函式會驗證它的參數。 如果*fd*不是有效的檔描述符,或者大小小於零,則調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
