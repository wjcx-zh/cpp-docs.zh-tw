---
title: srand | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- srand
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- srand
dev_langs:
- C++
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.assetid: 7bf56dc5-5692-4182-a3c1-18af98d2dd1a
caps.latest.revision: 12
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
ms.openlocfilehash: e86ea8aa561af584a6825d4225820aca7baeced2
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="srand"></a>srand
設定虛擬亂數產生器的起始種子值。  
  
## <a name="syntax"></a>語法  
  
```  
void srand(  
   unsigned int seed   
);  
```  
  
#### <a name="parameters"></a>參數  
 `seed`  
 虛擬亂數產生的種子  
  
## <a name="remarks"></a>備註  
 `srand` 函式會設定在目前執行緒中產生一系列虛擬隨機整數的起點。 若要重新初始化產生器來建立一系列相同的結果，請呼叫 `srand` 函式，並再次使用相同的 `seed` 引數。 `seed` 的任何其他值都會將產生器設為虛擬隨機序列中的不同起點。 `rand` 會擷取所產生的虛擬亂數。 在任何 `srand` 呼叫之前呼叫 `rand` 所產生的序列，與呼叫傳遞為 1 之 `seed` 的 `srand` 所產生的序列相同。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`srand`|\<stdlib.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [rand](../../c-runtime-library/reference/rand.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [rand](../../c-runtime-library/reference/rand.md)
