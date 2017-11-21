---
title: "offsetof 巨集 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
apitype: DLLExport
f1_keywords: offsetof
dev_langs: C++
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 47243b64519540397573a47180dca5eed25f4c57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="offsetof-macro"></a>offsetof 巨集
從其父結構開頭擷取成員的位移。  
  
## <a name="syntax"></a>語法  
  
```  
  
      size_t offsetof(  
   structName,  
   memberName   
);  
```  
  
#### <a name="parameters"></a>參數  
 *structName*  
 父資料結構的名稱。  
  
 `memberName`  
 要判斷其位移之父資料結構中成員的名稱。  
  
## <a name="return-value"></a>傳回值  
 `offsetof` 會傳回所指定成員從其父資料結構開頭的位移 (位元組)。 位元欄位並未定義它。  
  
## <a name="remarks"></a>備註  
 `offsetof` 巨集會將 `memberName` 從 *structName* 所指定結構開頭的位移 (位元組) 傳回類型為 `size_t` 的值。 您可以指定類型與 `struct` 關鍵字。  
  
> [!NOTE]
>  `offsetof` 不是函式，而且無法使用 C 原型進行描述。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`offsetof`|\<stddef.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)