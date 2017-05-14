---
title: "_ismbbgraph、_ismbbgraph_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbgraph_l
- _ismbbgraph
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
- _ismbbgraph
- _ismbbgraph_l
- ismbbgraph
- ismbbgraph_l
dev_langs:
- C++
helpviewer_keywords:
- _ismbbgraph_l function
- ismbbgraph_l function
- _ismbbgraph function
- ismbbgraph function
ms.assetid: b60db718-134f-4796-acc1-592d0b9efbb7
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 99ab02233eed70ab92e1aabcf567d9cfc244c101
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="ismbbgraph-ismbbgraphl"></a>_ismbbgraph、_ismbbgraph_l
判斷某個多位元組字元是否為圖形字元。  
  
## <a name="syntax"></a>語法  
  
```  
int _ismbbgraph (  
   unsigned int c   
);  
int _ismbbgraph_l (  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `c`  
 待測試整數。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 傳回非零值表示運算式：  
  
```  
( _PUNCT | _UPPER | _LOWER | _DIGIT ) || _ismbbkprint  
```  
  
 的 `c`為非零，否則會傳回 0。 針對任何地區設定相關行為，`_ismbbgraph` 會使用目前的地區設定。 `_ismbbgraph_l` 也相同，但是它會改用傳入的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_ismbbgraph`|\<mbctype.h>|  
|`_ismbbgraph_l`|\<mbctype.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)   
 [_ismbb 常式](../../c-runtime-library/ismbb-routines.md)
