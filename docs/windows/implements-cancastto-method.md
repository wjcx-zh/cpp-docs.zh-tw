---
title: 'Implements:: cancastto 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4fd6e6736c74e1ce895031e17c1d5268eb4ce646
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo 方法
取得指定的介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 參考介面識別碼。  
  
 `ppv`  
 如果成功，介面的指標會依指定`riid`。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，表示錯誤，例如 E_NOINTERFACE 的 HRESULT。  
  
## <a name="remarks"></a>備註  
 這是執行 QueryInterface 作業的內部協助程式函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Implements 結構](../windows/implements-structure.md)