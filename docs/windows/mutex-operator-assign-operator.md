---
title: "Mutex::operator= 運算子 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 運算子"
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mutex::operator= 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指派 （移動） 指定的 Mutex 物件傳遞至目前的 Mutex 物件。  
  
## <a name="syntax"></a>語法  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 右值參考，以 Mutex 物件。  
  
## <a name="return-value"></a>傳回值  
 目前的 Mutex 物件的參考。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 **移動語意** 區段 [右值參考宣告子︰ & （& s)](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** corewrappers.h  
  
 **命名空間︰** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另請參閱
 [Mutex 類別](../windows/mutex-class1.md)