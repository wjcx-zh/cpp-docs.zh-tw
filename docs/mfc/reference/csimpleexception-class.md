---
title: "CSimpleException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSimpleException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleException class"
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CSimpleException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是資源重要 MFC 例外狀況的基底類別。  
  
## 語法  
  
```  
  
class AFX_NOVTABLE CSimpleException : public CException  
  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleException::CSimpleException](../Topic/CSimpleException::CSimpleException.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleException::GetErrorMessage](../Topic/CSimpleException::GetErrorMessage.md)|提供有關發生錯誤的文字。|  
  
## 備註  
 `CSimpleException` 是資源重要 MFC 例外狀況的基底類別並處理錯誤資訊的擁有權和初始化。  下列類別會使用 `CSimpleException` 做為其基底類別:  
  
|||  
|-|-|  
|[CMemoryException 類別](../../mfc/reference/cmemoryexception-class.md)|記憶體不足例外狀況|  
|[CNotSupportedException 類別](../../mfc/reference/cnotsupportedexception-class.md)|要求不受支援的作業。|  
|[CResourceException 類別](../../mfc/reference/cresourceexception-class.md)|無法建立視窗的資源或找不到|  
|[CUserException 類別](../../mfc/reference/cuserexception-class.md)|表示資源的例外狀況找不到|  
|[CInvalidArgException 類別](../../mfc/reference/cinvalidargexception-class.md)|表示無效引數例外狀況。|  
  
 由於 `CSimpleException` 是抽象基底類別，所以您無法直接宣告 `CSimpleException` 物件。  相反地，您必須宣告衍生自的物件 \(例如上表中。  如果您宣告您的衍生類別，請使用先前的類別做為模型。  
  
 如需詳細資訊，請參閱 [CException 類別](../../mfc/reference/cexception-class.md) 主題和 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CSimpleException`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [例外狀況處理](../../mfc/exception-handling-in-mfc.md)