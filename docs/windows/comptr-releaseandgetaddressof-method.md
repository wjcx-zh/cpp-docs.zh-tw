---
title: "ComPtr::ReleaseAndGetAddressOf 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseAndGetAddressOf 方法"
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::ReleaseAndGetAddressOf 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

釋放介面與這個 ComPtr 然後擷取 [ptr\_](../windows/comptr-ptr-data-member.md) 資料成員的位址，包含已釋放的介面指標。  
  
## 語法  
  
```  
T** ReleaseAndGetAddressOf();  
```  
  
## 傳回值  
 ComPtr 的 [ptr\_](../windows/comptr-ptr-data-member.md) 資料成員的位址。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ComPtr 類別](../windows/comptr-class.md)   
 [ComPtr::ptr\_ 資料成員](../windows/comptr-ptr-data-member.md)