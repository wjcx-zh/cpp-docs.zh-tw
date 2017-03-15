---
title: "WeakReference::WeakReference 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference::WeakReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakReference，建構函式"
ms.assetid: 4959a9d7-78ea-423d-a46b-50d010d29fff
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# WeakReference::WeakReference 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 結構，而且不能直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
WeakReference();  
```  
  
## <a name="remarks"></a>備註  
 初始化的新執行個體 [WeakReference 類別](../windows/weakreference-class1.md)。  
  
 WeakReference 物件的強式參考指標初始化為 `nullptr`, ，和強式參考計數會初始化為 1。  
  
## <a name="requirements"></a>需求  
 **標頭︰** implements.h  
  
 **命名空間︰** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
    
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)