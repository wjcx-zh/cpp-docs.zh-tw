---
title: _write
ms.date: 4/2/2020
api_name:
- _write
- _o__write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: a616df570d266c335337d897da59a2a0ec69b40e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367386"
---
# <a name="_write"></a>_write

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

*Fd*<br/>
資料要寫入至其中之檔案的檔案描述項。

*緩衝區*<br/>
要寫入的資料。

*count*<br/>
位元組數。

## <a name="return-value"></a>傳回值

如果成功 **,_write**返回寫入的位元組數。 如果磁碟上的剩餘實際空間小於函數嘗試寫入磁碟的緩衝區大小 **,_write**失敗,並且不會將緩衝區的任何內容刷新到磁碟。 返回值 -1 表示錯誤。 若傳遞了無效的參數，此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數返回 **-1,errno**設置為三個值之一 **:EBADF,** 這意味著檔描述符無效或檔未打開以進行寫入;**ENOSPC**,這意味著設備上沒有足夠的空間用於操作;或**EINVAL**,這意味著*緩衝區*是空指標,或者*位元組的奇*數被傳遞到 Unicode 模式下的檔。

有關這些代碼和其他返回代碼的詳細資訊,請參閱[errno、_doserrno、_sys_errlist和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果在文字模式下打開檔,則每個換行符將替換為輸出中的回車換行對。 替換不會影響返回值。

在 Unicode 轉換模式下打開檔時,例如, 如果使用 **_open**或 **_sopen**以及包含 **_O_WTEXT、_O_U16TEXT**或 **_O_U8TEXT**的模式參數打開 **_O_WTEXT** *fd,* 或者如果使用**fopen**和包含 ccs_UNICODE、ccs_UTF-16LE 或**ccs_UTF-8**的模式更改為 Unicode 轉換 **_setmode**模式的模式**ccs=UNICODE****ccs=UTF-16LE**,則*緩衝區*將解釋為指向包含**UTF-16** **wchar_t數位的**指標。 嘗試以此模式寫入奇數位元組會導致參數驗證錯誤。

## <a name="remarks"></a>備註

**_write**函數將*緩衝區的計數*位元*buffer*組寫入 與*fd*關聯的檔中。 寫入作業會從與指定檔案相關之檔案指標 (若有的話) 的目前位置開始。 若檔案是開啟為以供附加，則作業會在檔案的目前結尾開始。 寫入操作後,檔指標將因寫入的位元組數而增加。

寫入文字模式下打開的檔時 **,_write**將 CTRL_Z 字元視為檔的邏輯結尾。 寫入裝置時 **,_write**將緩衝區中的 CTRL_Z 字元視為輸出終止符。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
            // An unrelated error occurred
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
