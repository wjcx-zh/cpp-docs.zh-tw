---
title: "CMemoryException Class | Microsoft Docs"
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
  - "CMemoryException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 例外狀況處理, 記憶體"
  - "CMemoryException class"
  - "例外狀況, memory type"
  - "memory exceptions"
  - "記憶體, 例外狀況處理"
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMemoryException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示記憶體不足的例外狀況。  
  
## 語法  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMemoryException::CMemoryException](../Topic/CMemoryException::CMemoryException.md)|建構 `CMemoryException` 物件。|  
  
## 備註  
 進一步資格不需要或不可能的。  記憶體不足例外狀況是由 **new**自動擲回。  使用 `malloc`，，例如，如果您撰寫自己的記憶體函式，則您必須負責擲回記憶體不足例外狀況。  
  
 如需 `CMemoryException`的詳細資訊，請參閱本文 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)