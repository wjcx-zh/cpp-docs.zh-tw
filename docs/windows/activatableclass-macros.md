---
title: "ActivatableClass 巨集 | Microsoft Docs"
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
  - "ActivatableClass"
  - "ActivatableClassWithFactory"
  - "ActivatableClassWithFactoryEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivatableClassWithFactory"
  - "ActivatableClass"
  - "ActivatableClassWithFactoryEx"
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivatableClass 巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擴展內部快取，其中包含可以建立指定類別的執行個體的 factory。  
  
## <a name="syntax"></a>語法  
  
```cpp  
ActivatableClass(  
   className  
);  
  
ActivatableClassWithFactory(  
   className,   
   factory  
);  
  
ActivatableClassWithFactoryEx(  
   className,   
   factory,   
   serverName  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `className`  
 若要建立類別的名稱。  
  
 `factory`  
 將會建立指定類別的執行個體的 factory。  
  
 `serverName`  
 指定模組中的處理站的子集名稱。  
  
## <a name="remarks"></a>備註  
 請勿使用這些巨集以傳統 COM 除非您使用 `#undef` 指示詞，以確保 **__WRL_WINRT_STRICT\_\_** 會移除巨集定義。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)