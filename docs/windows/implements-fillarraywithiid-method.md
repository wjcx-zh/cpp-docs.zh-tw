---
title: "Implements:: fillarraywithiid 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Implements::FillArrayWithIid
dev_langs: C++
helpviewer_keywords: FillArrayWithIid method
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a53a7eb9a05e1f4583c49b42fa10efdf1ee815ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="implementsfillarraywithiid-method"></a>Implements::FillArrayWithIid 方法
將插入至指定的陣列項目目前的第零個範本參數所指定的介面 ID。  
  
## <a name="syntax"></a>語法  
  
```  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### <a name="parameters"></a>參數  
 `index`  
 指出這項作業的起始陣列項目以零為起始的索引。 這項作業完成時，`index`都會遞增 1。  
  
 `iids`  
 IID 類型的陣列。  
  
## <a name="remarks"></a>備註  
 內部協助程式函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Implements 結構](../windows/implements-structure.md)