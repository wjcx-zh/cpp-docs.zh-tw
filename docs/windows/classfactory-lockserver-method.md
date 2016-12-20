---
title: "ClassFactory::LockServer 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::ClassFactory::LockServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LockServer 方法"
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ClassFactory::LockServer 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

遞增或遞減數目基礎物件，會追蹤目前的 ClassFactory 物件。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>參數  
 `fLock`  
 `true` 要遞增的追蹤的物件數目。 `false` 若要減少追蹤的物件數目。  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則，E_FAIL。  
  
## <a name="remarks"></a>備註  
 ClassFactory 會持續追蹤的物件中的基礎執行個體 [模組](../windows/module-class.md) 類別。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ClassFactory 類別](../windows/classfactory-class.md)