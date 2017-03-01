---
title: _set_controlfp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_controlfp
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
- set_controlfp
- _set_controlfp
dev_langs:
- C++
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
caps.latest.revision: 11
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: f7cf06b52624178a3d5bbe5907289eab7f57cbb5
ms.lasthandoff: 02/24/2017

---
# <a name="setcontrolfp"></a>_set_controlfp
設定浮點控制字組。  
  
## <a name="syntax"></a>語法  
  
```  
void __cdecl _set_controlfp(  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>參數  
 `newControl`  
 新的控制字組位元值。  
  
 `mask`  
 要設定之新控制字組位元的遮罩。  
  
## <a name="return-value"></a>傳回值  
 無。  
  
## <a name="remarks"></a>備註  
 `_set_controlfp` 與 `_control87` 類似，但只會將浮點控制字組設為 `newControl`。 值中的位元表示浮點控制狀態。 浮點控制狀態可讓程式變更浮點數學套件中的精確度、四捨五入和無限大模式。 您也可以使用 `_set_controlfp` 來遮罩或取消遮罩浮點例外狀況。 如需詳細資訊，請參閱 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)。  
  
 此函式已被取代，以編譯時[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)因為 common language runtime 僅支援預設浮點有效位數。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|相容性|  
|-------------|---------------------|-------------------|  
|`_set_controlfp`|\<float.h>|僅限 x86 處理器|  
  
 如需相容性詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [_clear87、_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87、_statusfp、_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)
