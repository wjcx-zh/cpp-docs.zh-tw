---
title: _dup、_dup2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _dup
- _dup2
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
- _dup2
- _dup
dev_langs:
- C++
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 820172e1e6ab4ad007c89b2b40f03512134f0f0d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215949"
---
# <a name="dup-dup2"></a>_dup、_dup2

建立已開啟之檔案的第二個檔案描述項 (**_dup**)，或重新指派檔案描述項 (**_dup2**)。

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

**_dup**傳回新的檔案描述項。 **_dup2**會傳回 0，表示作業成功。 如果發生錯誤時，每個函式會傳回-1 和集**errno**要**EBADF**如果檔案描述項無效，或以**EMFILE**如果沒有更多檔案描述項可用。 如果檔案描述項無效，函式也會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Dup**並 **_dup2**函式會將第二個檔案描述項關聯的目前開啟的檔案。 這些函數可以用來建立關聯的預先定義的檔案描述元，例如針對**stdout**，使用不同的檔案。 可使用任一檔案描述項來執行檔案作業。 建立新的描述項不會影響檔案所允許的存取類型。 **_dup**傳回下一個可用的檔案描述項，指定檔案。 **_dup2**強制*fd2*來參考相同的檔案*fd1*。 如果*fd2*關聯與開啟的檔案在呼叫時，會關閉該檔案。

兩者 **_dup**並 **_dup2**接受做為參數的檔案描述項。 若要將資料流 (`FILE *`) 至其中一個這些函式中，使用[_fileno](fileno.md)。 **Fileno**常式會傳回目前與指定的資料流相關聯的檔案描述項。 下列範例示範如何建立關聯**stderr** (定義為`FILE *`在 Stdio.h 中) 的檔案描述項：

```C
int cstderr = _dup( _fileno( stderr ));
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 主控台中，相關聯的標準資料流控制代碼**stdin**， **stdout**，並**stderr**，必須重新導向，C 執行階段函式才能使用它們在 UWP 應用程式. 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
