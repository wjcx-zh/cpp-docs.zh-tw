---
title: "COleDispatchException Class | Microsoft Docs"
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
  - "COleDispatchException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation, 例外狀況"
  - "COleDispatchException class"
  - "例外狀況, OLE"
  - "OLE exceptions, to IDispatch interface"
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDispatchException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理例外狀況的特定 OLE `IDispatch` 介面，為 OLE Automation 的主要部分。  
  
## 語法  
  
```  
class COleDispatchException : public CException  
```  
  
## 成員  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleDispatchException::m\_dwHelpContext](../Topic/COleDispatchException::m_dwHelpContext.md)|錯誤的說明內容。|  
|[COleDispatchException::m\_strDescription](../Topic/COleDispatchException::m_strDescription.md)|讓使用者錯誤描述。|  
|[COleDispatchException::m\_strHelpFile](../Topic/COleDispatchException::m_strHelpFile.md)|使用的說明檔和 `m_dwHelpContext`。|  
|[COleDispatchException::m\_strSource](../Topic/COleDispatchException::m_strSource.md)|產生例外狀況的應用程式。|  
|[COleDispatchException::m\_wCode](../Topic/COleDispatchException::m_wCode.md)|`IDispatch`\-特定錯誤碼。|  
  
## 備註  
 如 `CException` 從基底類別衍生的其他例外狀況類別， `COleDispatchException` 可以與 **THROW**`THROW_LAST`**TRY**、、、、和 **CATCH**`AND_CATCH``END_CATCH` 巨集。  
  
 一般而言，您應該呼叫 [AfxThrowOleDispatchException](../Topic/AfxThrowOleDispatchException.md) 建立並擲回 `COleDispatchException` 物件。  
  
 如需例外狀況的詳細資訊，請參閱 Microsoft 知識庫文件 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md) 和 [例外狀況:OLE 例外狀況。](../../mfc/exceptions-ole-exceptions.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleDispatchException`  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [MFC 範例 CALCDRIV](../../top/visual-cpp-samples.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDispatchDriver Class](../../mfc/reference/coledispatchdriver-class.md)   
 [COleException Class](../../mfc/reference/coleexception-class.md)