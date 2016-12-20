---
title: "Semaphore::Semaphore 建構函式 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "旗號，建構函式"
ms.assetid: 91c22ae7-181e-460d-ad40-70c3a53b26fd
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Semaphore::Semaphore 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Semaphore 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
explicit Semaphore(  
   HANDLE h  
);  
  
WRL_NOTHROW Semaphore(  
   _Inout_ Semaphore&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 控制代碼或號誌物件為右值參考。  
  
## <a name="requirements"></a>需求  
 **標頭︰** corewrappers.h  
  
 **命名空間︰** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另請參閱
 [Semaphore 類別](../windows/semaphore-class.md)