---
title: "WeakRef::operator&amp; 運算子 | Microsoft Docs"
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
  - "client/Microsoft::WRL::WeakRef::operator&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator& 運算子"
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakRef::operator&amp; 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳回表示目前物件的 WeakRef ComPtrRef 物件。  
  
## 語法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## 傳回值  
 表示目前物件的 WeakRef ComPtrRef 物件。  
  
## 備註  
 這是並不是要用在您的程式碼的內部 Helper 運算子。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [WeakRef 類別](../windows/weakref-class.md)