---
title: _get_wpgmptr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_wpgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
dev_langs:
- C++
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: d28d4df533d2c81250f45820f4a230cc45f64257
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="getwpgmptr"></a>_get_wpgmptr
取得 `_wpgmptr` 全域變數的目前值。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _get_wpgmptr(   
   wchar_t **pValue   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `pValue`  
 要以 `_wpgmptr` 變數的目前值填滿的字串指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回零；如果失敗，則傳回錯誤碼。 如果`pValue`為`NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_wpgmptr` 全域變數包含與處理相關聯的可執行檔的完整路徑做為寬字元字串。 如需詳細資訊，請參閱 [_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_get_wpgmptr`|\<stdlib.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另請參閱  
 [_get_pgmptr](../../c-runtime-library/reference/get-pgmptr.md)
