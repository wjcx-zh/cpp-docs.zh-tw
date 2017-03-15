---
title: "Module::GetActivationFactory 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::GetActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetActivationFactory 方法"
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Module::GetActivationFactory 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得模組的啟用 factory。  
  
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
 指定執行階段類別 IActivationFactory。  
  
 `serverName`  
 目前模組中的 class factory 子集的名稱。 指定伺服器名稱中使用 [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) 巨集，或指定 `nullptr` 取得預設伺服器名稱。  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則，HRESULT 傳回 GetActivationFactory。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
[模組類別](../windows/module-class.md)
 [ActivatableClass 巨集](../windows/activatableclass-macros.md)