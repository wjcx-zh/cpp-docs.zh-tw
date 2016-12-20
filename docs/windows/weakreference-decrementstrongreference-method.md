---
title: "WeakReference::DecrementStrongReference 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DecrementStrongReference 方法"
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakReference::DecrementStrongReference 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 結構，而且不能直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>備註  
 強式的參考計數遞減目前 WeakReference 物件。  
  
 當強式參考計數變成零時，強式參考設定為 `nullptr`。  
  
## <a name="return-value"></a>傳回值  
 遞減的強式參考計數。  
  
## <a name="requirements"></a>需求  
 **標頭︰** implements.h  
  
 **命名空間︰** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
[WeakReference 類別](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)