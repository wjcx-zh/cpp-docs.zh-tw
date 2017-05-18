---
title: "_rmdir、_wrmdir | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wrmdir
- _rmdir
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
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
dev_langs:
- C++
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
caps.latest.revision: 11
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 04b563468b9bc79ccd92d608dfeb4e7a3b85120a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="rmdir-wrmdir"></a>_rmdir、_wrmdir
刪除目錄。  
  
## <a name="syntax"></a>語法  
  
```  
  
      int _rmdir(  
   const char *dirname   
);  
int _wrmdir(  
   const wchar_t *dirname   
);  
```  
  
#### <a name="parameters"></a>參數  
 `dirname`  
 要移除之目錄的路徑。  
  
## <a name="return-value"></a>傳回值  
 如果已成功刪除目錄，所有這些函式都會傳回 0。 傳回值-1 表示錯誤和`errno`設為下列值之一︰  
  
 **ENOTEMPTY**  
 指定的路徑不是目錄、目錄不是空的，或是目錄是目前工作目錄或根目錄。  
  
 `ENOENT`  
 路徑無效。  
  
 **EACCES**  
 程式已有目錄的開啟控制代碼。  
  
 如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_rmdir` 函式會刪除 `dirname` 所指定的目錄。 目錄必須是空的，而且它不得是目前工作目錄或根目錄。  
  
 `_wrmdir` 是寬字元版本的 `_rmdir`；`dirname` 的 `_wrmdir` 引數是寬字元字串。 否則，`_wrmdir` 和 `_rmdir` 的行為即會相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_trmdir`|`_rmdir`|`_rmdir`|`_wrmdir`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_rmdir`|\<direct.h>|  
|`_wrmdir`|\<direct.h> 或 \<wchar.h>|  
  
 如需相容性詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_mkdir](../../c-runtime-library/reference/mkdir-wmkdir.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [_chdir、_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)
