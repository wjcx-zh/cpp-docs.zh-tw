---
title: "_splitpath_s、_wsplitpath_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wsplitpath_s
- _splitpath_s
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
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
dev_langs:
- C++
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9baa71ca1a3d624c08df8ff1cbd14a9386e1b83d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s、_wsplitpath_s
將一個路徑名稱分割為多個元件。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_splitpath、_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _splitpath_s(  
   const char * path,  
   char * drive,  
   size_t driveNumberOfElements,  
   char * dir,  
   size_t dirNumberOfElements,  
   char * fname,  
   size_t nameNumberOfElements,  
   char * ext,   
   size_t extNumberOfElements  
);  
errno_t _wsplitpath_s(  
   const wchar_t * path,  
   wchar_t * drive,  
   size_t driveNumberOfElements,  
   wchar_t *dir,  
   size_t dirNumberOfElements,  
   wchar_t * fname,  
   size_t nameNumberOfElements,  
   wchar_t * ext,  
   size_t extNumberOfElements  
);  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _splitpath_s(  
   const char *path,  
   char (&drive)[drivesize],  
   char (&dir)[dirsize],  
   char (&fname)[fnamesize],  
   char (&ext)[extsize]  
); // C++ only  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _wsplitpath_s(  
   const wchar_t *path,  
   wchar_t (&drive)[drivesize],  
   wchar_t (&dir)[dirsize],  
   wchar_t (&fname)[fnamesize],  
   wchar_t (&ext)[extsize]  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `path`  
 完整路徑。  
  
 [輸出] `drive`  
 後接冒號 (`:`) 的磁碟機代號。 如果您不需要磁碟機代號，則可以針對這個參數傳遞 `NULL`。  
  
 [輸入] `driveNumberOfElements`  
 以單一位元組或寬字元表示的 `drive` 緩衝區大小。 如果 `drive` 為 `NULL`，則這個值必須是 0。  
  
 [輸出] `dir`  
 目錄路徑，包括結尾斜線。 可以使用正斜線 (`/`) 和 (或) 反斜線 (`\`)。 如果您不需要目錄路徑，則可以針對這個參數傳遞 `NULL`。  
  
 [輸入] `dirNumberOfElements`  
 以單一位元組或寬字元表示的 `dir` 緩衝區大小。 如果 `dir` 為 `NULL`，則這個值必須是 0。  
  
 [輸出] `fname`  
 基底檔名 (不含副檔名)。 如果您不需要檔名，則可以針對這個參數傳遞 `NULL`。  
  
 [輸入] `nameNumberOfElements`  
 以單一位元組或寬字元表示的 `fname` 緩衝區大小。 如果 `fname` 為 `NULL`，則這個值必須是 0。  
  
 [輸出] `ext`  
 副檔名，包括前置句點 (**.**)。如果您不需要副檔名，則可以針對這個參數傳遞 `NULL`。  
  
 [輸入] `extNumberOfElements`  
 以單一位元組或寬字元表示的 `ext` 緩衝區大小。 如果 `ext` 是 `NULL`，則這個值必須是 0。  
  
## <a name="return-value"></a>傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|條件|傳回值|  
|---------------|------------------|  
|`path` 是 `NULL`|`EINVAL`|  
|`drive` 為 `NULL`，而 `driveNumberOfElements` 為非零|`EINVAL`|  
|`drive` 為非 `NULL`，而 `driveNumberOfElements` 為零|`EINVAL`|  
|`dir` 為 `NULL`，而 `dirNumberOfElements` 為非零|`EINVAL`|  
|`dir` 為非 `NULL`，而 `dirNumberOfElements` 為零|`EINVAL`|  
|`fname` 為 `NULL`，而 `nameNumberOfElements` 為非零|`EINVAL`|  
|`fname` 為非 `NULL`，而 `nameNumberOfElements` 為零|`EINVAL`|  
|`ext` 為 `NULL`，而 `extNumberOfElements` 為非零|`EINVAL`|  
|`ext` 為非 `NULL`，而 `extNumberOfElements` 為零|`EINVAL`|  
  
 如果發生上述任何狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
 如果有任何緩衝區太短而無法保留結果，這些函式會將所有緩衝區清除成空字串、將 `errno` 設定為 `ERANGE`，並傳回 `ERANGE`。  
  
## <a name="remarks"></a>備註  
 `_splitpath_s` 函式會將一個路徑分割為它的四個元件。 `_splitpath_s` 會自動的適當處理多位元組字串引數，根據目前使用中的多位元組字碼頁來辨識多位元組字串序列。 `_wsplitpath_s` 是 `_splitpath_s` 的寬字元版本；`_wsplitpath_s` 的引數是寬字元字串。 否則，這些函式的行為相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsplitpath_s`|`_splitpath_s`|`_splitpath_s`|`_wsplitpath_s`|  
  
 完整路徑的每個元件都會儲存在個別的緩衝區中；資訊清單常數 `_MAX_DRIVE`、`_MAX_DIR`、`_MAX_FNAME` 和 `_MAX_EXT` (定義於 STDLIB.H) 指定每個檔案元件允許的大小上限。 大於對應資訊清單常數的檔案元件會造成堆積損毀。  
  
 下表列出資訊清單常數的值。  
  
|名稱|值|  
|----------|-----------|  
|_MAX_DRIVE|3|  
|_MAX_DIR|256|  
|_MAX_FNAME|256|  
|_MAX_EXT|256|  
  
 如果完整路徑未包含元件 (例如，檔名)，則 `_splitpath_s` 會將空字串指派給對應的緩衝區。  
  
 在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_splitpath_s`|\<stdlib.h>|  
|`_wsplitpath_s`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 請參閱 [_makepath_s、_wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md) 的範例。  
  
## <a name="see-also"></a>請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_splitpath、_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)