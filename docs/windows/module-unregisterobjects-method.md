---
title: "Module::UnregisterObjects 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::UnregisterObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UnregisterObjects 方法"
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::UnregisterObjects 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取消註冊指定的模組中的物件，使其他應用程式無法連線到它們。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT UnregisterObjects(  
   ModuleBase* module,  
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>參數  
 `module`  
 模組的指標。  
  
 `serverName`  
 合格的名稱，指定此作業所影響的物件子集。  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果此作業成功。否則，錯誤 HRESULT 指出的原因，這項作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)