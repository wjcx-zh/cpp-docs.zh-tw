---
title: "WeakRef::WeakRef 建構函式 | Microsoft Docs"
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
  - "client/Microsoft::WRL::WeakRef::WeakRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakRef, 建構函式"
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakRef::WeakRef 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 WeakRef 類別的新執行個體。  
  
## 語法  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
#### 參數  
 `ptr`  
 現有物件的指標、參考、或 rvalue 參考初始化至目前 WeakRef 物件。  
  
## 備註  
 第一個建構函式會初始化空的 WeakRef 物件。  第二個建構函式會從指標的 WeakRef 物件加入至 IWeakReference 介面。  第三個建構函式會從參考的 WeakRef 物件加入至 ComPtr\< IWeakReference\> 物件。  第四和第五個建構函式會由另一個 WeakRef 物件的 WeakRef 物件。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [WeakRef 類別](../windows/weakref-class.md)