---
title: "CInternetException Class | Microsoft Docs"
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
  - "CInternetException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInternetException class"
  - "例外狀況處理, Internet operations"
  - "例外狀況, 網際網路"
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
caps.latest.revision: 22
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInternetException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示例外狀況與網際網路作業相關。  
  
## 語法  
  
```  
class CInternetException : public CException  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CInternetException::CInternetException](../Topic/CInternetException::CInternetException.md)|建構 `CInternetException` 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CInternetException::m\_dwContext](../Topic/CInternetException::m_dwContext.md)|內容與相關聯的值會導致例外狀況的作業。|  
|[CInternetException::m\_dwError](../Topic/CInternetException::m_dwError.md)|造成例外狀況的錯誤。|  
  
## 備註  
 `CInternetException` 類別包括兩個公用資料成員:一個錯誤碼負載與例外狀況，然後，保留其他網際網路應用程式的內容識別項與錯誤相關聯的。  
  
 如需網際網路應用程式的內容識別項的詳細資訊，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)