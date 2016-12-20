---
title: "ComPtr::operator Microsoft::WRL::Details::BoolType 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator Microsoft::WRL::Details::BoolType 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指出 ComPtr 是否管理介面的物件存留期 \(Lifetime\)。  
  
## 語法  
  
```  
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;  
```  
  
## 傳回值  
 如果介面與這個 ComPtr 有關聯， [BoolStruct::Member](../windows/boolstruct-member-data-member.md) 資料成員的位址，否則， `nullptr`。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ComPtr 類別](../windows/comptr-class.md)   
 [ComPtr::Get 方法](../windows/comptr-get-method.md)