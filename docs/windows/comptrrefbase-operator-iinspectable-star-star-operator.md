---
title: "ComPtrRefBase::operator IInspectable** 運算子 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator IInspectable** 運算子"
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRefBase::operator IInspectable** 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
operator IInspectable**() const;  
```  
  
## 備註  
 將目前 [ptr\_](../windows/comptrrefbase-ptr-data-member.md) 資料成員轉型至 IInspectable 介面指標的指標。  
  
 如果目前 ComPtrRefBase 不是衍生自 IInspectable，則會發出一個錯誤。  
  
 只有在 **\_\_WRL\_CLASSIC\_COM\_\_** 定義時轉型才可用。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [ComPtrRefBase 類別](../windows/comptrrefbase-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)