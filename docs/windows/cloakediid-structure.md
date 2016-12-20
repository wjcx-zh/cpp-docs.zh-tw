---
title: "CloakedIid 結構 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::CloakedIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CloakedIid 結構"
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CloakedIid 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示 RuntimeClass、實作和 ChainInterfaces 樣板指定的介面無法在 IID 清單中存取。  
  
## 語法  
  
```  
template<  
   typename T  
>  
struct CloakedIid : T;  
```  
  
#### 參數  
 `T`  
 隱藏的介面 \(隱匿\)。  
  
## 備註  
 下列範例顯示如何使用 CloakedIid：`struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`。  
  
## 繼承階層  
 `T`  
  
 `CloakedIid`  
  
## 需求  
 **標頭：**implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)