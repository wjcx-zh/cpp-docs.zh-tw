---
title: "Module::RegisterCOMObject 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::RegisterCOMObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegisterCOMObject 方法"
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Module::RegisterCOMObject 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

註冊一個或多個 COM 物件，使其他應用程式可以連接。  
  
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
 伺服器的完整名稱。  
  
 `clsids`  
 若要註冊的 Clsid 的陣列。  
  
 `factories`  
 IUnknown 介面，其可用性所發行的類別物件的陣列。  
  
 `cookies`  
 當作業完成時，物件的陣列的指標值，將類別識別已註冊的已。 這些值可於稍後用撤銷註冊。  
  
 `count`  
 若要註冊的 Clsid 數目。  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果 successfu;否則，例如指出原因 CO_E_OBJISREG HRESULT 作業失敗。  
  
## <a name="remarks"></a>備註  
 COM 物件會向 CLSCTX 列舉型別的 CLSCTX_LOCAL_SERVER 列舉值。  
  
 要註冊的物件的連接類型由目前的組合 `comflag` 樣板參數和 REGCLS 列舉型別的 REGCLS_SUSPENDED 列舉值。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)