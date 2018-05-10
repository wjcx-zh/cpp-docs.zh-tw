---
title: 'Chaininterfaces:: Fillarraywithiid 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: f1ce699c-dfb6-40a9-9ea0-e6703d3cf971
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7e6283b86b8e225771f259df9b5377fffa3667fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="chaininterfacesfillarraywithiid-method"></a>ChainInterfaces::FillArrayWithIid 方法
存放區所定義的介面 ID`I0`介面識別碼指定陣列中的指定位置的樣板參數。  
  
## <a name="syntax"></a>語法  
  
```  
__forceinline static void FillArrayWithIid(  
   _Inout_ unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### <a name="parameters"></a>參數  
 `index`  
 為索引值的指標`iids`陣列。  
  
 `iids`  
 介面 Id 的陣列。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ChainInterfaces 結構](../windows/chaininterfaces-structure.md)