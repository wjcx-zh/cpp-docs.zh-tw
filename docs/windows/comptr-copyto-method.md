---
title: 'Comptr:: Copyto 方法 |Microsoft Docs'
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
ms.openlocfilehash: 5b387d52c9ab7b1d9033ce70d36e9f0aa5e5b33e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642925"
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo 方法
複製目前或指定相關聯的介面與這個**ComPtr**至指定的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
### <a name="parameters"></a>參數  
 *U*  
 類型名稱。  
  
 *ptr*  
 這項作業完成時，所要求介面的指標。  
  
 *riid*  
 介面識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，HRESULT，指出為什麼隱含`QueryInterface`作業失敗。  
  
## <a name="remarks"></a>備註  
 第一次的函式會傳回與此相關聯的介面指標的複本**ComPtr**。 此函式一律會傳回 S_OK。  
  
 第二個函式會執行`QueryInterface`與此相關聯的介面上的作業**ComPtr**所指定的介面*riid*參數。  
  
 第三個函式會執行`QueryInterface`與此相關聯的介面上的作業**ComPtr**為基礎的介面*U*參數。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)