---
title: _close | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _close
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
f1_keywords: _close
dev_langs: C++
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f46560346718016af015410730696e766afa5c9a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="close"></a>_close
關閉檔案。  
  
## <a name="syntax"></a>語法  
  
```  
int _close(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>參數  
 `fd`  
 參考已開啟檔案的檔案描述項。  
  
## <a name="return-value"></a>傳回值  
 如果已成功關閉檔案，`_close` 會傳回 0。 傳回值-1 表示錯誤。  
  
## <a name="remarks"></a>備註  
 `_close` 函式會關閉與 `fd` 相關聯的檔案。  
  
 關閉檔案描述元和基礎 OS 檔案控制代碼。 因此，如果檔案一開始是使用 Win32 函式 `CreateFile` 所開啟並使用 `_open_osfhandle` 轉換成檔案描述元，則不需要呼叫 `CloseHandle`。  
  
 這個函式會驗證它的參數。 如果 `fd` 是不正確的檔案描述元，則會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，此函式會傳回 -1，並將 `errno` 設為 `EBADF`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_close`|\<io.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_open](../../c-runtime-library/reference/open-wopen.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [低層級 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chsize](../../c-runtime-library/reference/chsize.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_unlink、_wunlink](../../c-runtime-library/reference/unlink-wunlink.md)