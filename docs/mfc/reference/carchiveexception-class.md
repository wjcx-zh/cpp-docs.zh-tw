---
title: "CArchiveException Class | Microsoft Docs"
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
  - "CArchiveException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archive exceptions [C++]"
  - "CArchiveException class"
  - "exceptions [C++], archive"
  - "exceptions [C++], 序列化"
  - "序列化 [C++], 例外狀況"
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CArchiveException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示序列化例外狀況  
  
## 語法  
  
```  
class CArchiveException : public CException  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CArchiveException::CArchiveException](../Topic/CArchiveException::CArchiveException.md)|建構 `CArchiveException` 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CArchiveException::m\_cause](../Topic/CArchiveException::m_cause.md)|表示例外狀況的原因。|  
|[CArchiveException::m\_strFileName](../Topic/CArchiveException::m_strFileName.md)|對於這個例外狀況會指定檔案的名稱。|  
  
## 備註  
 `CArchiveException` 類別包含表示例外狀況的原因之一個公用資料成員。  
  
 `CArchiveException` 建構物件和中擲回 [CArchive](../../mfc/reference/carchive-class.md) 成員函式。  在 **CATCH** 運算式的範圍內，您可以存取這些物件。  讓程式碼與作業系統無關。  如需處理例外狀況的詳細資訊，請參閱 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CArchive Class](../../mfc/reference/carchive-class.md)   
 [AfxThrowArchiveException](../Topic/AfxThrowArchiveException.md)   
 [例外狀況處理](../../mfc/reference/exception-processing.md)