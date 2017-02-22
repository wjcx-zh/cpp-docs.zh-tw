---
title: "CFileException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFileException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFile class, exceptions of"
  - "CFileException class"
  - "例外狀況, file type"
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CFileException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示檔案相關的例外狀況。  
  
## 語法  
  
```  
class CFileException : public CException  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFileException::CFileException](../Topic/CFileException::CFileException.md)|建構 `CFileException` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFileException::ErrnoToException](../Topic/CFileException::ErrnoToException.md)|傳回與執行階段錯誤至數字的原因程式碼。|  
|[CFileException::GetErrorMessage](../Topic/CFileException::GetErrorMessage.md)|擷取描述例外狀況的訊息。|  
|[CFileException::OsErrorToException](../Topic/CFileException::OsErrorToException.md)|傳回造成程式碼具有作業系統錯誤碼的。|  
|[CFileException::ThrowErrno](../Topic/CFileException::ThrowErrno.md)|擲回根據執行階段錯誤數字的檔案例外狀況。|  
|[CFileException::ThrowOsError](../Topic/CFileException::ThrowOsError.md)|擲回以作業系統錯誤代碼的檔案例外狀況。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CFileException::m\_cause](../Topic/CFileException::m_cause.md)|包含可移植的程式碼與例外狀況原因的。|  
|[CFileException::m\_lOsError](../Topic/CFileException::m_lOsError.md)|包含相關作業系統錯誤代碼。|  
|[CFileException::m\_strFileName](../Topic/CFileException::m_strFileName.md)|包含檔案名稱的這個例外狀況的。|  
  
## 備註  
 `CFileException` 類別包含保留可攜式讓程式碼與作業系統特定的錯誤代碼的公用資料成員。  類別也提供靜態成員函式以擲回的檔案例外狀況並提供傳回作業系統錯誤和 C 執行階段錯誤的原因是程式碼。  
  
 `CFileException` 建構物件並擲回在 `CFile` 成員函式和在衍生類別中的成員函式。  在 **CATCH** 運算式的範圍內，您可以存取這些物件。  針對可攜性，請只使用讓程式碼取得例外狀況的原因。  如需例外狀況的詳細資訊，請參閱本文 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CFileException`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [例外狀況處理](../../mfc/reference/exception-processing.md)