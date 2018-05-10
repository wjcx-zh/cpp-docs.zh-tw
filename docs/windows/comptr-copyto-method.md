---
title: 'Comptr:: Copyto 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 680c1278ca2b17c7ea35e72946fb5d5030c5e7c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo 方法
複製與這個 ComPtr 的指定指標，相關聯的目前或指定的介面。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  

template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
#### <a name="parameters"></a>參數  
 `U`  
 類型名稱。  
  
 `ptr`  
 這項作業完成時，所要求介面的指標。  
  
 `riid`  
 介面識別碼。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，表示隱含 QueryInterface 作業失敗的原因的 HRESULT。  
  
## <a name="remarks"></a>備註  
 第一個函式會傳回要與這個 ComPtr 相關聯的介面指標的複本。 此函式一律傳回 S_OK。  
  
 第二個函式會執行與所指定的介面這個 ComPtr 相關聯的介面的 QueryInterface 運算`riid`參數。  
  
 第三個函式在執行與的基礎介面這個 ComPtr 相關聯的介面的 QueryInterface 運算`U`參數。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)