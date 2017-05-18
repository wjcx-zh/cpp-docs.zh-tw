---
title: _chdrive | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _chdrive
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
- chdrive
- _chdrive
dev_langs:
- C++
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
caps.latest.revision: 21
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
ms.openlocfilehash: 946f5bee25b093d024eecc030527be39ad1a0162
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="chdrive"></a>_chdrive
變更目前工作磁碟機。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int _chdrive(   
   int drive   
);  
```  
  
#### <a name="parameters"></a>參數  
 `drive`  
 1 到 26 範圍內指定目前工作磁碟機的整數 (1=A、2=B 等)。  
  
## <a name="return-value"></a>傳回值  
 若已成功變更目前工作磁碟機即為零 (0)；否則為 -1。  
  
## <a name="remarks"></a>備註  
 如果 `drive` 不在 1 到 26 的範圍內，則會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，**_chdrive** 函式會傳回 -1、將 `errno` 設為 `EACCES`，並將 `_doserrno` 設為 `ERROR_INVALID_DRIVE`。  
  
 **_chdrive** 函式不是安全執行緒，原因是其取決於本身不是安全執行緒的 **SetCurrentDirectory** 函式。 若要在多執行緒應用程式中安全地使用 **_chdrive**，您必須提供自己的執行緒同步處理。 如需詳細資訊，請前往 [MSDN Library](http://go.microsoft.com/fwlink/?LinkID=150542)，然後搜尋 **SetCurrentDirectory**。  
  
 **_chdrive** 函式只會變更目前工作磁碟機；**_chdir** 則會變更目前工作目錄。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|**_chdrive**|\<direct.h>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_getdrive](../../c-runtime-library/reference/getdrive.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [_chdir、_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getcwd、_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir、_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)
