---
title: 'Implements:: cancastto 方法 |Microsoft Docs'
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
ms.openlocfilehash: 53b17558998812895ece4b47f5de03700e502b8e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608939"
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
  
### <a name="parameters"></a>參數  
 *riid*  
 參考介面識別碼。  
  
 *ppv*  
 如果成功，介面的指標所指定*riid*。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，HRESULT，表示錯誤，例如 E_NOINTERFACE。  
  
## <a name="remarks"></a>備註  
 這是執行 QueryInterface 作業的內部協助程式函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Implements 結構](../windows/implements-structure.md)