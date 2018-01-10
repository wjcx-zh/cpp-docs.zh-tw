---
title: "ftell、_ftelli64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ftelli64
- ftell
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
- _ftelli64
- ftell
dev_langs: C++
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: df0feee9beb2b2fc5144974f1fc06ff2b8d02b80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ftell-ftelli64"></a>ftell、_ftelli64
取得檔案指標的目前位置。  
  
## <a name="syntax"></a>語法  
  
```  
long ftell(   
   FILE *stream   
);  
__int64 _ftelli64(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 以 `FILE` 結構為目標。  
  
## <a name="return-value"></a>傳回值  
 `ftell` 和 `_ftelli64` 傳回目前的檔案位置。 所傳回的值`ftell`和`_ftelli64`不一定能反映實際的位元組位移，在文字模式中開啟資料流的因為文字模式會導致歸位字元傳回換行字元轉譯。 使用`ftell`與`fseek`或`_ftelli64`與`_fseeki64`回到檔案位置正確。 錯誤時，`ftell`和`_ftelli64`叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，這些函數會傳回-1l; 此時和設定允許執行`errno`ERRNO 中定義的兩個常數的其中一個。H. `EBADF` 常數表示 `stream` 引數不是有效的檔案指標值，或未參考開啟的檔案。 `EINVAL` 表示無效的 `stream`。 在無法搜尋 (例如終端機和印表機) 的裝置上或 `stream` 未參考到開啟的檔案時，傳回值為未定義。  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `ftell`和`_ftelli64`函式會擷取與相關聯的目前位置的檔案指標 （如果有的話） `stream`。 位置以相對於資料流開頭的位移表示。  
  
 請注意，檔案因為附加資料而開啟時，目前的檔案位置取決於最後一個 I/O 作業，而不是下一次寫入的位置。 例如，如果開啟檔案以供附加，而最後一個作業為讀取，該檔案的位置是下一個讀取作業會開始的位置，而不是下一次寫入的開始位置。 (當開啟檔案以供附加時，該檔案會被移動到檔案結尾，任何寫入作業之前的位置。)如果開啟以供附加的檔案上尚未發生任何 I/O 作業，該檔案的位置是檔案的開頭。  
  
 在文字模式中，Ctrl+Z 會在輸入時被解譯成檔案結尾字元。 在檔案開啟供讀取/寫入時，`fopen` 和所有相關的常式檢查檔案結尾是否有 CTRL+Z，並在可能時將它移除。 之所以這麼做，是因為合併使用 `ftell` 和`fseek` 或 `_ftelli64` 和 `_fseeki64`以在 CTRL+Z 結尾的檔案內移動可能會讓 `ftell` 或 `_ftelli64` 在檔案結尾附近產生不當行為。  
  
 此函式執行期間會鎖定呼叫執行緒，因此為安全執行緒。 如需非鎖定版本，請參閱 `_ftell_nolock`。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|選擇性標頭|  
|--------------|---------------------|----------------------|  
|`ftell`|\<stdio.h>|\<errno.h>|  
|`_ftelli64`|\<stdio.h>|\<errno.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_ftell.c  
// This program opens a file named CRT_FTELL.C  
// for reading and tries to read 100 characters. It  
// then uses ftell to determine the position of the  
// file pointer and displays this position.  
  
#include <stdio.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long position;  
   char list[100];  
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )  
   {  
      // Move the pointer by reading data:   
      fread( list, sizeof( char ), 100, stream );  
      // Get position after read:   
      position = ftell( stream );  
      printf( "Position after trying to read 100 bytes: %ld\n",  
              position );  
      fclose( stream );  
   }  
}  
```  
  
```Output  
Position after trying to read 100 bytes: 100  
```  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)   
 [fseek、_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek、_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)