---
title: 'Asyncbase:: Trytransitiontoerror 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
helpviewer_keywords:
- TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97fcade98e82a289c172c7651f62f3de0394fe16
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError 方法
指出指定的錯誤程式碼是否可以修改的內部錯誤狀態。  
  
## <a name="syntax"></a>語法  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### <a name="parameters"></a>參數  
 `error`  
 錯誤 HRESULT。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果您的內部錯誤狀態已變更。否則， `false`。  
  
## <a name="remarks"></a>備註  
 這項作業會在錯誤狀態已設定為 S_OK 時，才修改錯誤狀態。 如果 「 錯誤 」 狀態已經是錯誤，已取消，完成，或已關閉，這項作業會有任何作用。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)