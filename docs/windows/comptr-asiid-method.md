---
title: "ComPtr::AsIID 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::AsIID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsIID 方法"
ms.assetid: d5a3cdb2-796d-4410-966a-847c0e8fb226
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::AsIID 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳回表示指定樣板的參數所識別的 ComPtr 介面 ID 的物件。  
  
## 語法  
  
```  
WRL_NOTHROW HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IUnknown>* p  
) const;  
```  
  
#### 參數  
 `riid`  
 介面 ID。  
  
 `p`  
 如果支援，則採用由`riid` 參數指定的雙重間接取值指標的介面，否則，會 IUnknown 的指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，則為表示錯誤的 HRESULT。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ComPtr 類別](../windows/comptr-class.md)