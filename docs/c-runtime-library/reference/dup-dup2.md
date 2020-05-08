---
title: _dup、_dup2
ms.date: 4/2/2020
api_name:
- _dup
- _dup2
- _o__dup
- _o__dup2
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
- _dup2
- _dup
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
ms.openlocfilehash: 6c635930fdbc8da550a2a32ea614e150fbeb08a8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915205"
---
# <a name="_dup-_dup2"></a>_dup、_dup2

為開啟的檔案建立第二個檔案描述項（**_dup**），或重新指派檔案描述項（**_dup2**）。

## <a name="syntax"></a>語法

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>參數

*fd*， *fd1*<br/>
參考已開啟檔案的檔案描述項。

*fd2*<br/>
任何檔案描述項。

## <a name="return-value"></a>傳回值

**_dup**會傳回新的檔案描述項。 **_dup2**會傳回0，表示成功。 如果發生錯誤，每個函式都會傳回-1，如果檔案描述元無效，則將**errno**設定為**EBADF** ，如果沒有其他可用的檔案描述項，則將設為**EMFILE** 。 如果檔案描述項無效，函式也會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Dup**和 **_dup2**函數會將第二個檔案描述項與目前開啟的檔案產生關聯。 這些函式可以用來將預先定義的檔案描述項（例如**stdout**的）與不同的檔案產生關聯。 可使用任一檔案描述項來執行檔案作業。 建立新的描述項不會影響檔案所允許的存取類型。 **_dup**會傳回指定檔案的下一個可用檔案描述項。 **_dup2**強制*fd2*參考與*fd1*相同的檔案。 如果在呼叫時， *fd2*與開啟的檔案相關聯，該檔案就會關閉。

**_Dup**和 **_dup2**都接受檔案描述元做為參數。 若要將資料流程（`FILE *`）傳遞給其中一個函數，請使用[_fileno](fileno.md)。 **Fileno**常式會傳回目前與指定資料流程相關聯的檔案描述項。 下列範例示範如何將**stderr** （定義為`FILE *`在 stdio.h 中）與檔案描述項產生關聯：

```C
int cstderr = _dup( _fileno( stderr ));
```

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

通用 Windows 平臺（UWP）應用程式中不支援主控台。 與主控台、 **stdin**、 **stdout**和**stderr**相關聯的標準資料流程控制碼必須重新導向，C 執行時間函式才能在 UWP 應用程式中使用它們。 如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_dup.c
// This program uses the variable old to save
// the original stdout. It then opens a new file named
// DataFile and forces stdout to refer to it. Finally, it
// restores stdout to its original state.

#include <io.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int old;
   FILE *DataFile;

   old = _dup( 1 );   // "old" now refers to "stdout"
                      // Note:  file descriptor 1 == "stdout"
   if( old == -1 )
   {
      perror( "_dup( 1 ) failure" );
      exit( 1 );
   }
   _write( old, "This goes to stdout first\n", 26 );
   if( fopen_s( &DataFile, "data", "w" ) != 0 )
   {
      puts( "Can't open file 'data'\n" );
      exit( 1 );
   }

   // stdout now refers to file "data"
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )
   {
      perror( "Can't _dup2 stdout" );
      exit( 1 );
   }
   puts( "This goes to file 'data'\n" );

   // Flush stdout stream buffer so it goes to correct file
   fflush( stdout );
   fclose( DataFile );

   // Restore original stdout
   _dup2( old, 1 );
   puts( "This goes to stdout\n" );
   puts( "The file 'data' contains:" );
   _flushall();
   system( "type data" );
}
```

```Output
This goes to stdout first
This goes to stdout

The file 'data' contains:
This goes to file 'data'
```

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
