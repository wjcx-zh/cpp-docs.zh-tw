---
title: _free_locale | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __free_locale
- free_locale
- _free_locale
dev_langs:
- C++
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1baa1458d3e799d2370092b7d8f96ee9fe4a359e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="freelocale"></a>_free_locale
釋放地區設定物件。  
  
## <a name="syntax"></a>語法  
  
```  
void _free_locale(  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `locale`  
 要釋放的地區設定物件。  
  
## <a name="remarks"></a>備註  
 `_free_locale` 函式用來釋放 `_get_current_locale` 或 `_create_locale` 呼叫所取得的地區設定物件。  
  
 已取代此函式的舊名稱 `__free_locale` (含兩個前置底線)。  
  
## <a name="requirements"></a>需求  
  
|`Routine`|必要的標頭|  
|---------------|---------------------|  
|`_free_locale`|\<locale.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [_get_current_locale](../../c-runtime-library/reference/get-current-locale.md)   
 [_create_locale、_wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)