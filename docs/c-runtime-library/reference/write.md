---
title: _write | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _write
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
apitype: DLLExport
f1_keywords:
- _write
dev_langs:
- C++
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fcf10428e354c9e31ed66a949ccf0a803f8137a6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="write"></a>_write

將資料寫入檔案。

## <a name="syntax"></a>語法

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>參數

*fd*<br/>
資料要寫入至其中之檔案的檔案描述項。

*buffer*<br/>
要寫入的資料。

*count*<br/>
位元組數。

## <a name="return-value"></a>傳回值

如果成功的話， **_write**傳回實際寫入的位元組數目。 如果磁碟上剩餘的實際空間小於函式嘗試寫入磁碟的緩衝區大小 **_write**失敗且不會清除任何緩衝區的內容至磁碟。 傳回值-1 表示錯誤。 若傳遞了無效的參數，此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函數會傳回-1 和**errno**設為三個值之一： **EBADF**、 表示的檔案描述項無效或未開啟檔案進行寫入。**ENOSPC**，的表示沒有任何作業; 在裝置上保留足夠的空間或**EINVAL**，這表示*緩衝區*是 null 指標或奇數*計數*的位元組傳送給寫入至以 Unicode 模式的檔案。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果在文字模式中開啟檔案時，每個換行字元會取代歸位字元-換行字元組在輸出中。 這種取代不會影響傳回值。

在 Unicode 轉譯模式中開啟檔案時，比方說，如果*fd*開啟使用 **_open**或 **_sopen**和模式參數，其包含 **_O_WTEXT**， **_O_U16TEXT**，或 **_O_U8TEXT**，或如果已開啟使用**fopen**和模式參數，其包含**ccs =UNICODE**， **ccs = UTF 16LE**，或**ccs = utf-8**，或如果模式變更為 Unicode 轉譯模式使用 **_setmode**—*緩衝區*解譯為陣列的指標**wchar_t**包含**utf-16**資料。 嘗試以此模式寫入奇數位元組會導致參數驗證錯誤。

## <a name="remarks"></a>備註

**_Write**函式寫入*計數*位元組從*緩衝區*與相關聯的檔案到*fd*。 寫入作業會從與指定檔案相關之檔案指標 (若有的話) 的目前位置開始。 若檔案是開啟為以供附加，則作業會在檔案的目前結尾開始。 經過寫入作業之後，檔案指標會隨著實際寫入的位元組數而增加。

在文字模式中開啟的檔案寫入時 **_write** CTRL + Z 字元視為邏輯的檔案結尾。 當寫入至裝置， **_write**會將 CTRL + Z 字元視為輸出結束字元緩衝區中。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_write**|\<io.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occured
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
