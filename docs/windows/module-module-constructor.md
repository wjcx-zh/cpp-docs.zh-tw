---
title: "Module::Module 建構函式 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::Module"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Module, 建構函式"
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::Module 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化模組類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
Module();  
```  
  
## <a name="remarks"></a>備註  
 這個建構函式會受到保護，且無法使用呼叫 `new` 關鍵字。 相反地，呼叫 [module:: getmodule 方法](../windows/module-getmodule-method.md) 或 [module:: create 方法](../windows/module-create-method.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)