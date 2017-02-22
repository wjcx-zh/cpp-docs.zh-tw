---
title: "Module::GetClassObject 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::GetClassObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetClassObject 方法"
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Module::GetClassObject 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取快取的 class factory。  
  
## <a name="syntax"></a>語法  
  
```  
 HRESULT GetClassObject(  
   REFCLSID clsid,  
   REFIID riid,  
   _Deref_out_ void **ppv,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `clsid`  
 類別識別碼。  
  
 `riid`  
 您要求的介面 ID。  
  
 `ppv`  
 傳回的物件指標。  
  
 `serverName`  
 在指定的伺服器名稱 `ActivatableClassWithFactory`, ，`ActivatableClassWithFactoryEx`, ，或 `ActivatableClass` 巨集，或 `nullptr` 取得預設伺服器名稱。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 不使用這個方法僅適用於 COM [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。 這個方法會公開只有 IClassFactory 方法。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)