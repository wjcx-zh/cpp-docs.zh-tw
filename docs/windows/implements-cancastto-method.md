---
title: "Implements::CanCastTo 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Implements::CanCastTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanCastTo 方法"
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implements::CanCastTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得指定介面的指標。  
  
## 語法  
  
```  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### 參數  
 `riid`  
 介面ID的參考。  
  
 `ppv`  
 如果成功，`riid`指定的介面的指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，表示錯誤的 HRESULT，例如 E\_NOINTERFACE。  
  
## 備註  
 這是執行 QueryInterface 作業的內部 Helper 函式。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Implements 結構](../windows/implements-structure.md)