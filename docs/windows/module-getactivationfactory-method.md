---
title: "Module:: getactivationfactory 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d5c5ca4d470f52ff9dde862cc99b10a3459cd0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory 方法
取得模組中啟動處理站。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW HRESULT GetActivationFactory(  
   _In_ HSTRING pActivatibleClassId,  
   _Deref_out_ IActivationFactory **ppIFactory,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pActivatibleClassId`  
 執行階段類別的 IID。  
  
 `ppIFactory`  
 指定的執行階段類別 IActivationFactory。  
  
 `serverName`  
 在目前的模組的 class factory 子集的名稱。 指定伺服器名稱中使用[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)巨集，或指定`nullptr`取得預設的伺服器名稱。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，GetActivationFactory 所傳回的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
[模組類別](../windows/module-class.md) [ActivatableClass 巨集](../windows/activatableclass-macros.md)