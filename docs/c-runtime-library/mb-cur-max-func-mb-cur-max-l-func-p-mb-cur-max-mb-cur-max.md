---
title: "___mb_cur_max_func、___mb_cur_max_l_func、__p___mb_cur_max、__mb_cur_max | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
apilocation:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
dev_langs:
- C++
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: c071ddafad89dc284aebea2dc49d74385feb91da
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="mbcurmaxfunc-mbcurmaxlfunc-pmbcurmax-mbcurmax"></a>___mb_cur_max_func、___mb_cur_max_l_func、__p___mb_cur_max、__mb_cur_max
內部 CRT 函式。 以多位元組字元為單位，擷取目前或指定之地區設定的最大位元組數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
int ___mb_cur_max_func(void);  
int ___mb_cur_max_l_func(_locale_t locale);  
int * __p___mb_cur_max(void);  
#define __mb_cur_max (___mb_cur_max_func())  
```  
  
#### <a name="parameters"></a>參數  
 Locale - 地區設定  
 要從中擷取結果的地區設定結構。 若此值為 null，則會使用目前執行緒地區設定。  
  
## <a name="return-value"></a>傳回值  
 目前或指定之地區設定的最大位元組數目 (以多位元組字元為單位)。  
  
## <a name="remarks"></a>備註  
 這是 CRT 用於從執行緒區域儲存區擷取 [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) 巨集之目前值的內部函式。 建議您為了可攜性在程式碼中使用 `MB_CUR_MAX` 巨集。  
  
 `__mb_cur_max` 巨集是呼叫 `___mb_cur_max_func()` 函式的便利方式。 `__p___mb_cur_max` 函式是針對與 Visual C++ 5.0 及更新版本的相容性所定義。  
  
 內部 CRT 函式是特別針對實作，且會依每個版本而有所不同。 不建議將此函式用於您的程式碼中。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>、\<stdlib.h>|  
  
## <a name="see-also"></a>另請參閱  
 [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
