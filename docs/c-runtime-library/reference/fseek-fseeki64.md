---
title: "fseek、_fseeki64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fseeki64
- fseek
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
- fseek
- _fseeki64
dev_langs:
- C++
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 0d0c0bf620f1b89b9decceed3db9434dae4f9437
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="fseek-fseeki64"></a>fseek、_fseeki64
將檔案指標移至指定的位置。  
  
## <a name="syntax"></a>語法  
  
```  
int fseek(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標。  
  
 `offset`  
 來自 `origin` 的位元組數目。  
  
 `origin`  
 初始位置。  
  
## <a name="return-value"></a>傳回值  
 如果成功，`fseek` 和 `_fseeki64` 會傳回 0。 否則，它會傳回非零值。 在無法搜尋的裝置上，傳回的值為未定義。 如果 `stream` 是 Null 指標，或如果 `origin` 不是其中一個如下所述的允許值，則`fseek` 和 `_fseeki64` 會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` ，並傳回 -1。  
  
## <a name="remarks"></a>備註  
 `fseek`和`_fseeki64`函式的移動檔案指標 （如果有的話） 相關聯`stream`至新位置`offset`位元組從`origin`。 資料流的下一個作業會在新位置進行。 在開啟以供更新的資料流中，下一項作業可能是讀取或寫入。 引數的原點必須是下列常數之一，於 STDIO.H 中定義：  
  
 `SEEK_CUR`  
 檔案指標的目前位置。  
  
 `SEEK_END`  
 檔案結尾。  
  
 `SEEK_SET`  
 檔案開頭。  
  
 您可以使用 `fseek` 和 `_fseeki64` 將指標重新放置在檔案中的任何位置。 指標也可以放置在超過檔案結尾的位置。 `fseek`和`_fseeki64`清除檔案結尾指標，並取消任何之前的效果`ungetc`針對呼叫`stream`。  
  
 檔案因為附加資料而開啟時，目前的檔案位置取決於最後一個 I/O 作業，而不是下一次寫入的位置。 如果開啟以供附加的檔案上尚未發生任何 I/O 作業，該檔案的位置是檔案的開頭。  
  
 在文字模式中開啟資料流的`fseek`和`_fseeki64`有限使用，因為會造成歸位字元與換行字元傳回翻譯`fseek`和`_fseeki64`來產生非預期的結果。 唯一`fseek`和`_fseeki64`保證可以在文字模式開啟的資料流上運作的作業︰  
  
-   相對於任何原點值，位移為 0 的搜尋。  
  
-   搜尋從位移的值與檔案的開頭傳回呼叫`ftell`時使用`fseek`或`_ftelli64`時使用`_fseeki64`。  
  
 此外，在文字模式中，Ctrl+Z 會在輸入時被解譯成檔案結尾字元。 在檔案開啟供讀取/寫入時，`fopen` 和所有相關的常式檢查檔案結尾是否有 CTRL+Z，並在可能時將它移除。 之所以這麼做，是因為合併使用 `fseek` 和`ftell` 或 `_fseeki64` 和 `_ftelli64`以在 CTRL+Z 結尾的檔案內移動可能會讓 `fseek` 或 `_fseeki64` 在檔案結尾附近產生不當行為。  
  
 當 CRT 開啟以位元順序標記 (BOM) 開頭的檔案時，檔案指標的位置在 BOM 之後 (也就是在檔案實際內容的開頭)。 如果您需要 `fseek` 檔案的開頭，請使用 `ftell` 取得初始位置，並 `fseek` 至該位置，而不是位置 0。  
  
 此函式於執行期間鎖定其他執行緒，因此為安全執行緒。 如需非鎖定版本，請參閱 [_fseek_nolock、_fseeki64_nolock](../../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`fseek`|\<stdio.h>|  
|`_fseeki64`|\<stdio.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_fseek.c  
// This program opens the file FSEEK.OUT and  
// moves the pointer to the file's beginning.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[81];  
   int  result;  
  
   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )  
   {  
      printf( "The file fseek.out was not opened\n" );  
      return -1;  
   }  
   fprintf( stream, "The fseek begins here: "  
                    "This is the file 'fseek.out'.\n" );  
   result = fseek( stream, 23L, SEEK_SET);  
   if( result )  
      perror( "Fseek failed" );  
   else  
   {  
      printf( "File pointer is set to middle of first line.\n" );  
      fgets( line, 80, stream );  
      printf( "%s", line );  
    }  
   fclose( stream );  
}  
```  
  
```Output  
File pointer is set to middle of first line.  
This is the file 'fseek.out'.  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [ftell、_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [_lseek、_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)
