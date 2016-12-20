---
title: "CComPtr Class | Microsoft Docs"
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
  - "CComPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComPtr class"
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理的 COM 介面指標的智慧型指標類別。  
  
## 語法  
  
```  
  
      template<  
   class T   
>  
class CComPtr  
```  
  
#### 參數  
 `T`  
 指定指標型別 COM 介面的值。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComPtr::CComPtr](../Topic/CComPtr::CComPtr.md)|建構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CComPtr::operator \=](../Topic/CComPtr::operator%20=.md)|將成員指標的指標。|  
  
## 備註  
 ATL 會 `CComPtr` 和 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) 處理 COM 介面指標。  兩個從衍生的型別， [CComPtrBase](../../atl/reference/ccomptrbase-class.md)，而且同時執行自動參考計數。  
  
 **CComPtr** 和 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) 類別可以藉由執行自動參考計數減少記憶體遺漏 \(Memory Leak\)。  下列兩個函式執行相同的邏輯作業，但是請注意，第二個版本可能會如何比較不容易出錯的使用 **CComPtr** 類別:  
  
 [!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/CPP/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/CPP/ccomptr-class_2.cpp)]  
  
 在偵錯組建中，程式碼追蹤的連結 atlsd.lib。  
  
## 繼承階層架構  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [CComPtr::CComPtr](../Topic/CComPtr::CComPtr.md)   
 [CComQIPtr::CComQIPtr](../Topic/CComQIPtr::CComQIPtr.md)   
 [Class Overview](../../atl/atl-class-overview.md)