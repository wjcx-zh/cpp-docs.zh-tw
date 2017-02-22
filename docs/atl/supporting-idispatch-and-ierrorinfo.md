---
title: "支援 IDispatch 和 IErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IErrorInfo"
  - "IDispatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 中的 IDispatch 類別支援"
  - "IDispatchImpl 類別"
  - "ATL 中的 IErrorInfo 類別支援"
  - "ISupportErrorInfoImpl 方法"
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 支援 IDispatch 和 IErrorInfo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您在物件上使用樣板類別 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 提供所有雙重介面的 `IDispatch Interface` 部分的預設實作。  
  
 如果您使用的 `IErrorInfo` 介面報告錯誤回用戶端，則您的物件必須支援 `ISupportErrorInfo Interface` 介面。  樣板類別 [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) 提供簡易的方法來實作它，則只有在物件產生錯誤的單一介面。  
  
## 請參閱  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)