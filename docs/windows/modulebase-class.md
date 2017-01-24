---
title: "ModuleBase 類別 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::ModuleBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ModuleBase 類別"
ms.assetid: edce7591-6893-46f7-94a7-382827775548
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ModuleBase 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 結構，而且不能直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>備註  
 表示基底類別 [模組](../windows/module-class.md) 類別。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[Modulebase:: Modulebase 建構函式](../windows/modulebase-modulebase-constructor.md)|初始化模組類別的執行個體。|  
|[ModuleBase:: ~ ModuleBase 解構函式](../windows/modulebase-tilde-modulebase-destructor.md)|Deinitializes 模組類別的目前執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Modulebase:: Decrementobjectcount 方法](../windows/modulebase-decrementobjectcount-method.md)|實作時，遞減模組所追蹤的物件數目。|  
|[Modulebase:: Incrementobjectcount 方法](../windows/modulebase-incrementobjectcount-method.md)|實作時，遞增模組所追蹤的物件的數目。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ModuleBase`  
  
## <a name="requirements"></a>需求  
 **標頭︰** implements.h  
  
 **命名空間︰** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)