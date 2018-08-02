---
title: 'Asyncbase:: Get_errorcode 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- get_ErrorCode method
ms.assetid: 50b4f8a2-9a21-4ea0-bb5d-7ff524d62aea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fab750ce655add3ccdac9d955e1e3a36e46f8cc5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465125"
---
# <a name="asyncbasegeterrorcode-method"></a>AsyncBase::get_ErrorCode 方法
擷取目前的非同步作業的錯誤碼。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   get_ErrorCode  
)(HRESULT* errorCode) override;  
```  
  
#### <a name="parameters"></a>參數  
 *errorCode*  
 儲存目前的錯誤程式碼位置。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，如果目前的非同步作業已關閉的 E_ILLEGAL_METHOD_CALL。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)