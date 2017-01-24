---
title: "CResourceException Class | Microsoft Docs"
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
  - "CResourceException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CResourceException class"
  - "例外狀況, 資源"
  - "resource allocation exception"
  - "resource exceptions"
  - "資源 [C++], 配置"
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CResourceException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生的，當視窗找不到或無法配置所要求的資源。  
  
## 語法  
  
```  
class CResourceException : public CSimpleException  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CResourceException::CResourceException](../Topic/CResourceException::CResourceException.md)|建構 `CResourceException` 物件。|  
  
## 備註  
 進一步資格不需要或不可能的。  
  
 如需使用 `CResourceException`的詳細資訊，請參閱本文 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CResourceException`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)