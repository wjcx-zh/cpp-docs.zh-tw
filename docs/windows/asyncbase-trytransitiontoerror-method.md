---
title: 'Asyncbase:: Trytransitiontoerror 方法 |Microsoft Docs'
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
ms.openlocfilehash: fc677304ae7ab61e6726366869e85f731cd92484
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463203"
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
 *error*  
 錯誤的 HRESULT。  
  
## <a name="return-value"></a>傳回值  
 **真**如果內部錯誤狀態已變更，否則**false**。  
  
## <a name="remarks"></a>備註  
 這項作業會在錯誤狀態已設為 S_OK 時，才修改錯誤狀態。 如果錯誤的狀態已取消、 已完成，或關閉的錯誤，這項作業會有任何作用。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)