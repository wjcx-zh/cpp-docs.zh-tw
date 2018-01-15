---
title: _get_printf_count_output | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_printf_count_output
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
- get_printf_count_output
- _get_printf_count_output
dev_langs: C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 78c48423be0bc642b96c7a46d75f101e183c73fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output
表示 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函式是否支援 `%n` 格式。  
  
## <a name="syntax"></a>語法  
  
```  
int _get_printf_count_output();  
```  
  
## <a name="return-value"></a>傳回值  
 如果支援 `%n` 則為非零，如果 `%n` 不受支援則為 0。  
  
## <a name="remarks"></a>備註  
 如果 `%n` 不受支援 (預設值)，在任何 `printf` 函式的格式字串中遭遇 `%n` 時，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果`%n`已啟用支援 (請參閱[_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)) 然後`%n`中所述的行為[格式規格語法： printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_get_printf_count_output`|\<stdio.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 請參閱[_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)的範例。  
  
## <a name="see-also"></a>請參閱  
[_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)  
