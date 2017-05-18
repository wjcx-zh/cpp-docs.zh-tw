---
title: "_splitpath、_wsplitpath | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wsplitpath
- _splitpath
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
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
dev_langs:
- C++
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: bbd6a163df9daf8e699f3ecf52325786fe89d8ea
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="splitpath-wsplitpath"></a>_splitpath、_wsplitpath
將一個路徑名稱分割為多個元件。 這些函式已有更安全的版本可供使用，請參閱 [_splitpath_s、_wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
void _splitpath(  
   const char *path,  
   char *drive,  
   char *dir,  
   char *fname,  
   char *ext   
);  
void _wsplitpath(  
   const wchar_t *path,  
   wchar_t *drive,  
   wchar_t *dir,  
   wchar_t *fname,  
   wchar_t *ext   
);  
```  
  
#### <a name="parameters"></a>參數  
 `path`  
 完整路徑。  
  
 `drive`  
 後接冒號 (`:`) 的磁碟機代號。 如果您不需要磁碟機代號，則可以針對這個參數傳遞 `NULL`。  
  
 `dir`  
 目錄路徑，包括結尾斜線。 可以使用正斜線 (`/`) 和 (或) 反斜線 (`\`)。 如果您不需要目錄路徑，則可以針對這個參數傳遞 `NULL`。  
  
 `fname`  
 基底檔名 (無副檔名)。 如果您不需要檔名，則可以針對這個參數傳遞 `NULL`。  
  
 `ext`  
 副檔名，包括前置句點 (`.`)。 如果您不需要副檔名，則可以針對這個參數傳遞 `NULL`。  
  
## <a name="remarks"></a>備註  
 `_splitpath` 函式會將一個路徑分割為它的四個元件。 `_splitpath` 會根據目前使用中的多位元組字碼頁，自動將多位元組字元字串引數處理為適當且可辨識的多位元組字元序列。 `_wsplitpath` 是 `_splitpath` 的寬字元版本；`_wsplitpath` 的引數是寬字元字串。 除此之外，這些函式的行為相同。  
  
 **安全性提示**這些函式可能會帶來緩衝區滿溢問題所引發的威脅。 緩衝區滿溢問題是系統攻擊常見的方法，會造成權限無故提高。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。 這些函式已有更安全的版本可供使用，請參閱 [_splitpath_s、_wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsplitpath`|`_splitpath`|`_splitpath`|`_wsplitpath`|  
  
 完整路徑的每個元件都會儲存在個別的緩衝區中；資訊清單常數 `_MAX_DRIVE`、`_MAX_DIR`、`_MAX_FNAME` 和 `_MAX_EXT` (定義於 STDLIB.H) 指定每個檔案元件的大小上限。 大於對應資訊清單常數的檔案元件會造成堆積損毀。  
  
 每個緩衝區都必須與其對應的資訊清單常數一樣大，以避免潛在緩衝區滿溢。  
  
 下表列出資訊清單常數的值。  
  
|名稱|值|  
|----------|-----------|  
|_MAX_DRIVE|3|  
|_MAX_DIR|256|  
|_MAX_FNAME|256|  
|_MAX_EXT|256|  
  
 如果完整路徑未包含元件 (例如，檔名)，則 `_splitpath` 會將空字串指派給對應的緩衝區。  
  
 您可以針對任何不需要之 `path` 以外的參數，將 `NULL` 傳遞至 `_splitpath`。  
  
 如果 `path` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`errno` 會設為 `EINVAL`，且此函式會傳回 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_splitpath`|\<stdlib.h>|  
|`_wsplitpath`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_makepath](../../c-runtime-library/reference/makepath-wmakepath.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [_splitpath_s、_wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)
