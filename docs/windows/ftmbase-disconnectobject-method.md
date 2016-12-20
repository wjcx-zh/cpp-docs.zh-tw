---
title: "FtmBase::DisconnectObject 方法 | Microsoft Docs"
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
  - "ftm/Microsoft::WRL::FtmBase::DisconnectObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DisconnectObject 方法"
ms.assetid: 33253eec-3a65-4e72-8525-0249245a4790
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::DisconnectObject 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

強制釋放物件的所有外部連接。  物件的伺服器在關閉之前呼叫這個方法之物件的實作。  
  
## 語法  
  
```  
STDMETHODIMP DisconnectObject(  
   __in DWORD dwReserved  
) override;  
```  
  
#### 參數  
 `dwReserved`  
 保留以備將來之用；必須為零。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，表示錯誤的 HRESULT。  
  
## 需求  
 **標題:** ftm.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)