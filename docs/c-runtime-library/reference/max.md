---
title: __max | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- __max
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
f1_keywords:
- max
- __max
dev_langs:
- C++
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1868106e4224e05d661aba5bfb0ed4dca31f508a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="max"></a>__max
傳回兩個值的較大值。  
  
## <a name="syntax"></a>語法  
  
```  
type __max(  
   type a,  
   type b   
);  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 任何數值資料類型。  
  
 `a, b`  
 要比較之任何數字類型的值。  
  
## <a name="return-value"></a>傳回值  
 `__max` 傳回其引數的較大引數。  
  
## <a name="remarks"></a>備註  
 `__max` 巨集比較兩個值並傳回較大值。 引數可以是帶正負號或不帶正負號的任何數值資料類型。 引數和傳回值必須屬於相同的資料類型。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`__max`|\<stdlib.h>|  
  
## <a name="example"></a>範例  
 如需詳細資訊，請參閱 [__min](../../c-runtime-library/reference/min.md) 的範例。  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [__min](../../c-runtime-library/reference/min.md)