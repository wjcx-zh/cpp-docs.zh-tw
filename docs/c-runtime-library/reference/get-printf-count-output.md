---
title: _get_printf_count_output | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_printf_count_output
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
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 9f45a13d9911e82b2b624689fa6b9e5eb4b20d97
ms.lasthandoff: 02/24/2017

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
 如果 `%n` 不受支援 (預設值)，在任何 `printf` 函式的格式字串中遭遇 `%n` 時，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果 `%n` 啟用支援 (請參閱 [_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md))，則 `%n` 的行為會如 [printf 類型欄位字元](../../c-runtime-library/printf-type-field-characters.md)中所述。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_get_printf_count_output`|\<stdio.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱[_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)的範例。  
  
## <a name="net-framework-equivalent"></a>NET Framework 對等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。
