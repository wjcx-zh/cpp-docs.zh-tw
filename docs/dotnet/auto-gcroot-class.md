---
title: "auto_gcroot 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::auto_gcroot"
  - "msclr.auto_gcroot"
  - "auto_gcroot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_gcroot"
ms.assetid: b5790912-265d-463e-a486-47302e91042a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# auto_gcroot 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可用於內嵌虛擬控制代碼的原生型別的自動的資源 \(例如 [auto\_ptr 類別](../standard-library/auto-ptr-class.md)\)。  
  
## 語法  
  
```  
template<typename _element_type>  
class auto_gcroot;  
```  
  
#### 參數  
 `_element_type`  
 將內嵌的 Managed 型別。  
  
## 需求  
 **標頭檔** \<msclr \\ auto\_gcroot.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [auto\_gcroot](../dotnet/auto-gcroot.md)   
 [auto\_gcroot 成員](../dotnet/auto-gcroot-members.md)   
 [如何：以原生類型宣告控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)   
 [auto\_handle 類別](../dotnet/auto-handle-class.md)