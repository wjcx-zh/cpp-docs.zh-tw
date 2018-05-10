---
title: 'Comptr:: Asweak 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak method
ms.assetid: 23e29dcd-39cb-423f-abe6-6df4428213bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f262191304471a171e9c3370046dbdac71869cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="comptrasweak-method"></a>ComPtr::AsWeak 方法
擷取目前物件的弱式參考。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AsWeak(  
   _Out_ WeakRef* pWeakRef  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pWeakRef`  
 這項作業完成時，弱式參考物件的指標。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)