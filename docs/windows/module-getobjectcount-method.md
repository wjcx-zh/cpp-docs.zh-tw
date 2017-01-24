---
title: "Module::GetObjectCount 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::GetObjectCount"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetObjectCount 方法"
ms.assetid: 9fe29747-7e7f-40f2-9f6b-9a206b17fa8e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::GetObjectCount 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取這個模組所管理的物件數目。  
  
## <a name="syntax"></a>語法  
  
```  
virtual long GetObjectCount() const;  
```  
  
## <a name="return-value"></a>傳回值  
 目前此模組所管理之物件的數目。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)