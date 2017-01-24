---
title: "Mutex::Mutex 建構函式 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Mutex, 建構函式"
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mutex::Mutex 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Mutex 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 控制代碼，則 Mutex 物件的控制代碼，為右值參考。  
  
## <a name="remarks"></a>備註  
 第一個建構函式初始化 Mutex 物件，從指定的控制代碼。 第二個建構函式初始化從指定的控制代碼、 Mutex 物件，然後將 mutex 的擁有權移至目前的 Mutex 物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** corewrappers.h  
  
 **命名空間︰** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另請參閱
 [Mutex 類別](../windows/mutex-class1.md)