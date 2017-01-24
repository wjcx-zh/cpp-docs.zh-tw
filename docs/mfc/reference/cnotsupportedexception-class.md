---
title: "CNotSupportedException Class | Microsoft Docs"
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
  - "CNotSupportedException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNotSupportedException class"
  - "例外狀況, not supported"
  - "unsupported features"
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CNotSupportedException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示一個要求的結果不受支援的功能的例外狀況。  
  
## 語法  
  
```  
class CNotSupportedException : public CSimpleException  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CNotSupportedException::CNotSupportedException](../Topic/CNotSupportedException::CNotSupportedException.md)|建構 `CNotSupportedException` 物件。|  
  
## 備註  
 進一步資格不需要或不可能的。  
  
 如需使用 `CNotSupportedException`的詳細資訊，請參閱本文 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CNotSupportedException`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)