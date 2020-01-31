---
title: _write
ms.date: 11/04/2016
api_name:
- _write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: 5eaee64c1bf6ad4b4d59c3a7b1a1434741e74454
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821788"
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

*fd*<br/>
資料要寫入至其中之檔案的檔案描述項。

*buffer*<br/>
要寫入的資料。

*count*<br/>
位元組數。

## <a name="return-value"></a>傳回值

如果成功， **_write**會傳回寫入的位元組數目。 如果磁片上剩餘的實際空間小於函數嘗試寫入磁片的緩衝區大小， **_write**會失敗，且不會將任何緩衝區的內容排清到磁片。 傳回值-1 表示發生錯誤。 若傳遞了無效的參數，此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回-1，並將**errno**設定為下列三個值的其中一個： **EBADF**，這表示檔案描述元無效或檔案未開啟以供寫入;**ENOSPC**，這表示裝置上沒有足夠的空間可進行操作;或**EINVAL**，這表示*緩衝區*是 null 指標，或者傳遞了奇數的位元組*計數*，以 Unicode 模式寫入檔案。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果檔案是在文字模式中開啟，則每個換行字元都會以輸出中的換行傳回分行符號來取代。 取代並不會影響傳回值。

以 Unicode 轉譯模式開啟檔案時，例如如果*fd*是使用 **_open**或 **_sopen**以及包含 **_O_WTEXT**、 **_O_U16TEXT**或 **_O_U8TEXT**的模式參數來開啟，或者它是使用**fopen**和包含**ccs = Unicode**、 **ccs = utf-utf-16le**或**ccs = utf-8**的模式參數開啟，或如果使用 **_setmode**將模式變更為 Unicode 轉譯模式，則會將*buffer*視為指向包含**utf-16**資料之**wchar_t**的陣列。 嘗試以此模式寫入奇數位元組會導致參數驗證錯誤。

## <a name="remarks"></a>備註

**_Write**函式會將*計數*位元組從*緩衝區*寫入與*fd*相關聯的檔案中。 寫入作業會從與指定檔案相關之檔案指標 (若有的話) 的目前位置開始。 若檔案是開啟為以供附加，則作業會在檔案的目前結尾開始。 在寫入作業之後，檔案指標會以寫入的位元組數來增加。

寫入以文字模式開啟的檔案時， **_write**會將 CTRL + Z 字元視為檔的邏輯尾。 寫入裝置時， **_write**會將緩衝區中的 CTRL + Z 字元視為輸出結束字元。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_write**|\<io.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
