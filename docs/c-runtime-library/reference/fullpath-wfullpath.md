---
title: "_fullpath、_wfullpath | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fullpath
- _wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
dev_langs:
- C++
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
caps.latest.revision: 18
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
ms.openlocfilehash: 7641c3cdc2a437d2c65f964ca6b1220992d11bca
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="fullpath-wfullpath"></a>_fullpath、_wfullpath
為指定的相對路徑名稱建立絕對路徑或完整路徑名稱。  
  
## <a name="syntax"></a>語法  
  
```  
char *_fullpath(   
   char *absPath,  
   const char *relPath,  
   size_t maxLength   
);  
wchar_t *_wfullpath(   
   wchar_t *absPath,  
   const wchar_t *relPath,  
   size_t maxLength   
);  
```  
  
#### <a name="parameters"></a>參數  
 `absPath`  
 包含絕對路徑名稱或完整路徑名稱之緩衝區的指標，或為 NULL。  
  
 `relPath`  
 相對路徑名稱。  
  
 `maxLength`  
 絕對路徑名稱緩衝區的最大長度 (`absPath`)。 此長度針對 `_fullpath` 使用位元組，但針對 `wchar_t` 使用寬字元 (`_wfullpath`)。  
  
## <a name="return-value"></a>傳回值  
 每個函式會傳回包含絕對路徑名稱之緩衝區的指標 (`absPath`)。 若有錯誤 (例如，傳入 `relPath` 的值包含無效或是找不到的磁碟機代號，或是建立的絕對路徑名稱 (`absPath`) 的長度大於`maxLength`)，則函式會傳回 `NULL`。  
  
## <a name="remarks"></a>備註  
 `_fullpath`函式會擴展中的相對路徑名稱`relPath`為完整或絕對路徑和儲存區中的這個名稱`absPath`。 如果 `absPath` 為 NULL，`malloc` 會被用來配置具有足夠長度儲存路徑名稱的緩衝區。 釋放這個緩衝區是呼叫端的責任。 相對路徑名稱指定從目前的位置到另一個位置的路徑 (例如目前的工作目錄：「.」)。 絕對路徑名稱是相對路徑名稱的擴充狀態，其表示從檔案系統根目錄到達所需位置的完整路徑。 不同於 `_makepath`，`_fullpath` 可用來取得相對路徑的絕對路徑名稱 (`relPath`)，其名稱中包含「./」或「../」。  
  
 例如，若要使用 C 執行階段常式，應用程式必須包含具有常式宣告的標頭檔。 每個標頭檔以相對的方式包含檔案位置的陳述式參考 (從應用程式的工作目錄)︰  
  
```  
#include <stdlib.h>  
```  
  
 當檔案的絕對路徑 (實際的檔案系統位置) 可能是：  
  
```  
\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h  
```  
  
 `_fullpath` 會自動的適當處理多位元組字串引數，根據目前使用中的多位元組字碼頁來辨識多位元組字串序列。 `_wfullpath` 是 `_fullpath` 的寬字元版本；`_wfullpath` 的字串引數是寬字元字串。 `_wfullpath` 和 `_fullpath` 的行為完全相同，不同之處在於`_wfullpath` 不會處理多位元組字元字串。  
  
 如果 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC` 兩者都已定義，對 `_fullpath` 和 `_wfullpath` 的呼叫會由對 `_fullpath_dbg` 和 `_wfullpath_dbg` 的呼叫取代，以便進行偵錯記憶體配置。 如需詳細資訊，請參閱 [_fullpath_dbg、_wfullpath_dbg](../../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)。  
  
 如果 `maxlen` 小於或等於 0，則這個函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `NULL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfullpath`|`_fullpath`|`_fullpath`|`_wfullpath`|  
  
 如 果`absPath` 緩衝區為 `NULL`，`_fullpath` 會呼叫 [malloc](../../c-runtime-library/reference/malloc.md) 以配置緩衝區，並會忽略 `maxLength` 引數。 呼叫端必須負責視需要取消配置這個緩衝區 (使用 [free](../../c-runtime-library/reference/free.md))。 如果 `relPath` 引數指定磁碟機，此磁碟機的目前目錄會與路徑合併。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`_fullpath`|\<stdlib.h>|  
|`_wfullpath`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_fullpath.c  
// This program demonstrates how _fullpath  
// creates a full path from a partial path.  
  
#include <stdio.h>  
#include <conio.h>  
#include <stdlib.h>  
#include <direct.h>  
  
void PrintFullPath( char * partialPath )  
{  
   char full[_MAX_PATH];  
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )  
      printf( "Full path is: %s\n", full );  
   else  
      printf( "Invalid path\n" );  
}  
  
int main( void )  
{  
   PrintFullPath( "test" );  
   PrintFullPath( "\\test" );  
   PrintFullPath( "..\\test" );  
}  
```  
  
```Output  
Full path is: C:\Documents and Settings\user\My Documents\test  
Full path is: C:\test  
Full path is: C:\Documents and Settings\user\test  
```  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_getcwd、_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdcwd、_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_splitpath、_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)
