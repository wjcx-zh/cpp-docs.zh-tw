---
title: _close | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _close
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _close
dev_langs:
- C++
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e49906a1ea0bf66400a6ac753c5d4041bc47217c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="close"></a>_close

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

**_close**如果檔案已成功關閉時，則傳回 0。 傳回值-1 表示錯誤。

## <a name="remarks"></a>備註

**_Close**函式會關閉與相關聯的檔案*fd*。

關閉檔案描述元和基礎 OS 檔案控制代碼。 因此，不需要呼叫**CloseHandle**如果使用的 Win32 函式原本開啟檔案**CreateFile** ，轉換為使用檔案描述元 **_open_osfhandle**.

這個函式會驗證它的參數。 如果*fd*是不正確的檔案描述項無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函數會傳回-1 和**errno**設**EBADF**。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_open](open-wopen.md) 的範例。

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[dup、dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_unlink、_wunlink](unlink-wunlink.md)<br/>
