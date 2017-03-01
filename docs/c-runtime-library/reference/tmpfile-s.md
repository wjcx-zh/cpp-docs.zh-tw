---
title: tmpfile_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- tmpfile_s
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
- tmpfile_s
dev_langs:
- C++
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 04ccc149a214ccad7007ef140e87a5c20986b343
ms.lasthandoff: 02/24/2017

---
# <a name="tmpfiles"></a>tmpfile_s
建立暫存檔。 它是 [tmpfile](../../c-runtime-library/reference/tmpfile.md) 版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t tmpfile_s(  
   FILE** pFilePtr  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `pFilePtr`  
 用來儲存所產生資料流指標位址的指標位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 0，如果失敗，則為錯誤碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`pFilePtr`|**傳回值**|`pFilePtr` **的內容**。|  
|----------------|----------------------|---------------------------------|  
|`NULL`|`EINVAL`|未變更|  
  
 如果發生上述參數驗證錯誤，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`errno` 會設定為 `EINVAL`，且傳回值為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `tmpfile_s` 函式會建立暫存檔案，並將該資料流的指標放在 `pFilePtr` 引數中。 暫存檔案建立於根目錄。 若要在非根目錄的目錄建立暫存檔案，請使用 [tmpnam_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md) 或 [tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 搭配 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)。  
  
 如果無法開啟檔案，`tmpfile_s` 會將 `NULL` 寫入至 `pFilePtr` 參數。 此暫存檔案會在檔案關閉時、程式正常終止時，或在呼叫 `_rmtmp` 時自動刪除，假設目前的工作目錄不會變更。 暫存檔案以 `w+b` (二進位讀取/寫入) 模式開啟。  
  
 如果您嘗試使用 `tmpfile_s.` 超過 `TMP_MAX_S` 次呼叫，就會發生失敗 (請參閱 STDIO.H)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`tmpfile_s`|\<stdio.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
> [!NOTE]
>  這個範例需要系統管理權限才能在 Windows Vista 上執行。  
  
```  
// crt_tmpfile_s.c  
// This program uses tmpfile_s to create a  
// temporary file, then deletes this file with _rmtmp.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char tempstring[] = "String to be written";  
   int  i;  
   errno_t err;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      err = tmpfile_s(&stream);  
      if( err )  
         perror( "Could not open new temporary file\n" );  
      else  
         printf( "Temporary file %d was created\n", i );  
   }  
  
   // Remove temporary files.  
   printf( "%d temporary files deleted\n", _rmtmp() );  
}  
```  
  
```Output  
Temporary file 1 was created  
Temporary file 2 was created  
Temporary file 3 was created  
3 temporary files deleted  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_rmtmp](../../c-runtime-library/reference/rmtmp.md)   
 [_tempnam、_wtempnam、tmpnam、_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)
