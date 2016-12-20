---
title: "CInvalidArgException Class | Microsoft Docs"
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
  - "CInvalidArgException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInvalidArgException class"
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInvalidArgException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示無效引數例外狀況。  
  
## 語法  
  
```  
  
class CInvalidArgException : public CSimpleException  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CInvalidArgException::CInvalidArgException](../Topic/CInvalidArgException::CInvalidArgException.md)|建構函式。|  
  
## 備註  
 `CInvalidArgException` 物件表示無效引數例外狀況。  
  
 如需例外狀況處理的詳細資訊，請參閱 [CException 類別](../../mfc/reference/cexception-class.md) 主題和 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CInvalidArgException`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSimpleException Class](../../mfc/reference/csimpleexception-class.md)