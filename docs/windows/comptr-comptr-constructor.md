---
title: "ComPtr::ComPtr 建構函式 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::ComPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtr，建構函式"
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::ComPtr 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 ComPtr 類別的新執行個體。  多載提供預設值，複製，移動和轉換建構函式。  
  
## 語法  
  
```  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
#### 參數  
 `U`  
 `other` 參數的型別。  
  
 `other`  
 型別 `U` 的物件。  
  
## 傳回值  
  
## 備註  
 第一個建構函式是預設建構函式，隱含建立空的物件。  第二個建構函式指定 [\_\_nullptr](../windows/nullptr-cpp-component-extensions.md)，明確建立空的物件。  
  
 第三個建構函式會從指標指定的物件建立物件。  
  
 第四和第五個建構函式是複製建構函式。  第五個建構函式會複製物件如果其可以轉換為目前型別。  
  
 第六個和第七個建構函式是用來移動建構函式。  第七個建構函式會移動物件如果其可以轉換為目前型別。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ComPtr 類別](../windows/comptr-class.md)