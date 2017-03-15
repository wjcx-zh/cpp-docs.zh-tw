---
title: "Module::RegisterObjects 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::RegisterObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegisterObjects 方法"
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Module::RegisterObjects 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

註冊 COM 或 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 讓其他應用程式可以連接至這些物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RegisterObjects(  
   ModuleBase* module,   
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>參數  
 `module`  
 Com 或 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 物件。  
  
 `serverName`  
 建立物件的伺服器名稱。  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則，HRESULT 值，指出的原因，作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
## <a name="see-also"></a>另請參閱
[模組類別](../windows/module-class.md)