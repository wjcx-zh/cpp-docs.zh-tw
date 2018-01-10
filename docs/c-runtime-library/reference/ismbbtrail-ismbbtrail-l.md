---
title: "_ismbbtrail、_ismbbtrail_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbtrail
- _ismbbtrail_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ismbbtrail
- ismbbtrail
- _ismbbtrail_l
- ismbbtrail_l
dev_langs: C++
helpviewer_keywords:
- ismbbtrail_l function
- _ismbbtrail function
- _ismbbtrail_l function
- ismbbtrail function
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e5c20e436e7b51b1c4e5463fb56165ae24c264d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ismbbtrail-ismbbtraill"></a>_ismbbtrail、_ismbbtrail_l
判斷位元組是否為多位元組字元的尾端位元組。  
  
## <a name="syntax"></a>語法  
  
```  
int _ismbbtrail(  
   unsigned int c   
);  
int _ismbbtrail_l(  
   unsigned int c,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>參數  
 `c`  
 要測試的整數。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果整數 `c` 是多位元組字元的第二個位元組，則 `_ismbbtrail` 會傳回非零值。 例如，僅限在字碼頁 932 中，有效範圍是 0x40 到 0x7E 以及 0x80 到 0xFC。  
  
## <a name="remarks"></a>備註  
 `_ismbbtrail` 使用目前的地區設定進行地區設定相關行為。 `_ismbbtrail_l` 也相同，但是它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_ismbbtrail`|\<mbctype.h> 或 \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|  
|`_ismbbtrail_l`|\<mbctype.h> 或 \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|  
  
 \* 針對此測試條件的資訊清單常數。  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)   
 [_ismbb 常式](../../c-runtime-library/ismbb-routines.md)