---
title: 'Module:: registercomobject 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c002dd64049006c8ee74c709c585a3a9d0f253a5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873975"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject 方法
註冊一個或多個 COM 物件，讓其他應用程式可以連接到它們。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW virtual HRESULT RegisterCOMObject(  
   const wchar_t* serverName,  
   IID* clsids,  
   IClassFactory** factories,  
   DWORD* cookies,  
   unsigned int count);  
  
```  
  
#### <a name="parameters"></a>參數  
 `serverName`  
 伺服器的完整限定名稱。  
  
 `clsids`  
 若要註冊的 Clsid 的陣列。  
  
 `factories`  
 正在發行其可用性的類別物件的 IUnknown 介面的陣列。  
  
 `cookies`  
 當作業完成時，物件的陣列的類別識別的值的指標，已註冊。 這些值稍後用撤銷註冊。  
  
 `count`  
 若要註冊的 Clsid 數目。  
  
## <a name="return-value"></a>傳回值  
 S_OK 如果 successfu;否則，例如指出的原因的 CO_E_OBJISREG 作業失敗的 HRESULT。  
  
## <a name="remarks"></a>備註  
 COM 物件會註冊 CLSCTX 列舉型別的 CLSCTX_LOCAL_SERVER 列舉值。  
  
 目前的組合所指定的連接已註冊的物件類型`comflag`樣板參數和 REGCLS 列舉型別的 REGCLS_SUSPENDED 列舉值。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [Module 類別](../windows/module-class.md)