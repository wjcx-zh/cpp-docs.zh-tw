---
title: "_fsopen、_wfsopen | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wfsopen"
  - "_fsopen"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wfsopen"
  - "fsopen"
  - "tfsopen"
  - "_tfsopen"
  - "_wfsopen"
  - "_fsopen"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fsopen 函式"
  - "_tfsopen 函式"
  - "_wfsopen 函式"
  - "檔案共用 [C++]"
  - "檔案 [C++], 開啟"
  - "fsopen 函式"
  - "開啟檔案, 資料流"
  - "tfsopen 函式"
  - "wfsopen 函式"
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fsopen、_wfsopen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以檔案共用開啟資料流。  
  
## 語法  
  
```  
FILE *_fsopen(   
   const char *filename,  
   const char *mode,  
   int shflag   
);  
FILE *_wfsopen(   
   const wchar_t *filename,  
   const wchar_t *mode,  
   int shflag   
);  
```  
  
#### 參數  
 `filename`  
 要開啟的檔案之名稱。  
  
 `mode`  
 允許的存取類型。  
  
 `shflag`  
 允許的共用類型。  
  
## 傳回值  
 這些函式中每一個都會傳回資料流的指標。  null 指標值表示錯誤。  如果 `filename` 或 `mode` 為 `NULL` 或空字串，則這些函式會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_fsopen` 函式會開啟 `filename` 指定的檔案做為資料流，並準備此檔案，以供共用讀取或寫入使用 \(如同此模式和 `shflag` 引數所指定\)。  `_wfsopen` 是 `_fsopen` 的寬字元版本；`_wfsopen` 的 `filename` 和 `mode` 引數是寬字元字串。  否則，`_wfsopen` 和 `_fsopen` 的行為即會相同。  
  
 字元字串 `mode` 會指定對檔案要求的存取類型，如下表所示。  
  
|詞彙|定義|  
|--------|--------|  
|`"r"`|開啟以讀取。  如果檔案不存在或找不到，`_fsopen` 呼叫就會失敗。|  
|`"w"`|開啟空白檔案以寫入。  如果指定的檔案已存在，其內容將被終結。|  
|`"a"`|開啟以寫入該檔案結尾 \(附加\)；如果該檔案不存在，便會先建立檔案。|  
|`"r+"`|開啟以進行讀取和寫入。  \(檔案必須存在。\)|  
|`"w+"`|開啟空白檔案以進行讀取和寫入。  如果指定的檔案已存在，其內容將被終結。|  
|`"a+"`|開啟以寫入和附加；如果該檔案不存在，便會先建立檔案。|  
  
 請小心使用 `"w"` 和 `"w+"` 類型，因為它們可以終結現有的檔案。  
  
 使用 `"a"` 或 `"a+"` 存取類型開啟檔案時，所有寫入作業都會在檔案結尾進行。  檔案指標可以使用 `fseek` 或 `rewind` 重新調整位置，但是在執行任何寫入作業之前，永遠會移回至檔案結尾。  因此，無法覆寫現有資料。  指定 `"r+"`、`"w+"` 或 `"a+"` 存取類型時，同時允許讀取和寫入 \(表示檔案要開啟以供更新\)。  不過，在讀取和寫入之間切換時，必須有中間的 [fsetpos](../../c-runtime-library/reference/fsetpos.md)、[fseek](../../c-runtime-library/reference/fseek-fseeki64.md) 或 [rewind](../../c-runtime-library/reference/rewind.md) 作業。  如有需要，可以針對 `fsetpos` 或 `fseek` 作業指定目前位置。  除了上面的值之外，可以將下列字元包含在 `mode`，指定新行和檔案管理的轉譯模式。  
  
|詞彙|定義|  
|--------|--------|  
|`t`|以文字 \(已轉譯\) 模式開啟檔案  在此模式中，會將歸位字元\-換行字元 \(CR\-LF\) 組合在輸入中轉譯成單行換行字元 \(LF\)，且會將 LF 字元在輸出中轉譯為 CR\-LF 組合。  此外，Ctrl\+Z 會在輸入中解譯成檔案結尾字元。  在為了讀取或讀取\/寫入而開啟的檔案中，`_fsopen` 會盡可能檢查檔案結尾是否有 Ctrl\+Z，並加以移除。  之所以這樣做，是因為使用 `fseek` 和 `ftell` 在以 Ctrl\+Z 結束的檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不當行為。|  
|`b`|在二進位 \(未轉譯\) 模式中開啟檔案；會隱藏上述轉譯。|  
|`S`|指定針對但不限於磁碟的循序存取進行快取最佳化。|  
|`R`|指定針對但不限於磁碟的隨機存取進行快取最佳化。|  
|`T`|指定檔案做為暫存檔。  可能的話，不將其清除至磁碟。|  
|`D`|指定檔案做為暫存檔。  當最後一個檔案指標關閉時，將其刪除。|  
  
 如果 `mode` 中未指定 `t` 或 `b`，則轉譯模式由預設模式變數 `_fmode` 定義。  如果引數前置 `t` 或 `b`，則函式失敗並傳回 `NULL`。  如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
 引數 `shflag` 是常數運算式，其中包含定義在 Share.h 中的下列資訊清單常數之一。  
  
|詞彙|定義|  
|--------|--------|  
|`_SH_COMPAT`|設定 16 位元應用程式的相容性模式。|  
|`_SH_DENYNO`|允許讀取和寫入存取。|  
|`_SH_DENYRD`|拒絕對該檔案的讀取存取。|  
|`_SH_DENYRW`|拒絕對該檔案的讀取和寫入存取。|  
|`_SH_DENYWR`|拒絕對該檔案的寫入存取。|  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tfsopen`|`_fsopen`|`_fsopen`|`_wfsopen`|  
  
## 需求  
  
|函式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_fsopen`|\<stdio.h\>|\<share.h\><br /><br /> 針對 `shflag` 參數的資訊清單常數。|  
|`_wfsopen`|\<stdio.h\> 或 \<wchar.h\>|\<share.h\><br /><br /> 針對 `shflag` 參數的資訊清單常數。|  
  
## 範例  
  
```  
// crt_fsopen.c  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <share.h>  
  
int main( void )  
{  
   FILE *stream;  
  
   // Open output file for writing. Using _fsopen allows us to  
   // ensure that no one else writes to the file while we are  
   // writing to it.  
    //  
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )  
   {  
      fprintf( stream, "No one else in the network can write "  
                       "to this file until we are done.\n" );  
      fclose( stream );  
   }  
   // Now others can write to the file while we read it.  
   system( "type outfile" );  
}  
```  
  
  **直到我們完成之前，網路上其他人都不可以寫入這個檔案。**   
## .NET Framework 對等用法  
  
-   [System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)  
  
-   <xref:System.IO.FileStream.%23ctor%2A>  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_fdopen、\_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [\_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [\_sopen、\_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)