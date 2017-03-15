---
title: _get_osfhandle | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: 14
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
ms.openlocfilehash: 2e96f911e6784744eb539f6ce2b1961102d9869d
ms.lasthandoff: 02/24/2017

---
# <a name="getosfhandle"></a>_get_osfhandle
擷取與指定的檔案描述元相關聯的作業系統檔案控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
intptr_t _get_osfhandle(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>參數  
 `fd`  
 現有的檔案描述元。  
  
## <a name="return-value"></a>傳回值  
 如果 `fd` 有效，則為作業系統檔案控制代碼。 否則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則此函式會傳回 `INVALID_HANDLE_VALUE` (-1)，並將 `errno` 設為 `EBADF`，表示無效的檔案控制代碼。  
  
## <a name="remarks"></a>備註  
 若要關閉以 `_get_osfhandle` 開啟的檔案，請呼叫 `_close`。 呼叫 `_close` 也會關閉基礎控制代碼，因此不必在原始控制代碼上呼叫 Win32 函式 `CloseHandle`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_get_osfhandle`|\<io.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)
