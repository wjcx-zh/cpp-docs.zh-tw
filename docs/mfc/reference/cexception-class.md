---
title: "CException Class | Microsoft Docs"
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
  - "CException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchiveException class, 基底類別"
  - "CDaoException class, 基底類別"
  - "CDBException class, 基底類別"
  - "CException class"
  - "CFileException class, 基底類別"
  - "CInternetException class, 基底類別"
  - "CMemoryException class, 基底類別"
  - "CNotSupportedException class, 基底類別"
  - "COleDispatchException class, 基底類別"
  - "COleException class, 基底類別"
  - "CResourceException class, 基底類別"
  - "CUserException class"
  - "例外狀況, classes for"
  - "巨集, 例外狀況處理"
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
caps.latest.revision: 22
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有例外狀況的基底類別在 MFC 程式庫。  
  
## 語法  
  
```  
class AFX_NOVTABLE CException : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CException::CException](../Topic/CException::CException.md)|建構 `CException` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CException::Delete](../Topic/CException::Delete.md)|刪除 `CException` 物件。|  
|[CException::ReportError](../Topic/CException::ReportError.md)|在訊息方塊中顯示一個錯誤訊息向使用者報告。|  
  
## 備註  
 由於 `CException` 是抽象基底類別。您無法直接建立物件， `CException` 您必須建立衍生類別的物件。  如果您需要建立自己的 `CException`樣式類別，請使用做為模型上面所列的其中一個衍生類別。  請確定您的衍生類別 \(Derived Class\) 會使用 `IMPLEMENT_DYNAMIC`。  
  
 衍生類別及其描述如下所列:  
  
|||  
|-|-|  
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|資源重要 MFC 例外狀況的基底類別|  
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|無效引數例外狀況|  
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|記憶體不足例外狀況|  
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|要求不受支援的作業。|  
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|檔案的特定例外狀況。|  
|[CFileException](../../mfc/reference/cfileexception-class.md)|檔案的特定例外狀況。|  
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|無法建立視窗的資源或找不到|  
|[COleException](../../mfc/reference/coleexception-class.md)|OLE 例外狀況。|  
|[CDBException](../../mfc/reference/cdbexception-class.md)|資料庫例外狀況 \(即引發的 MFC 資料庫類別的例外狀況是以 Open 開放式資料庫連接\)|  
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|OLE Automation 分派 \(\) 例外狀況。|  
|[CUserException](../../mfc/reference/cuserexception-class.md)|例外狀況以表示找不到資源|  
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|資料存取物件 \(也就是例外狀況發生的 DAO 類別\) 的例外狀況|  
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|網際網路例外狀況 \(即引發為網際網路類別\) 的例外狀況。|  
  
 這些例外狀況的用意是要與 [擲回。](../Topic/THROW%20\(MFC\).md)、 [THROW\_LAST](../Topic/THROW_LAST.md)、 [嘗試。](../Topic/TRY.md)、 [catch](../Topic/CATCH.md)， [AND\_CATCH](../Topic/AND_CATCH.md)和 [END\_CATCH](../Topic/END_CATCH.md) 巨集。  如需例外狀況的詳細資訊，請參閱 [例外狀況處理。](../../mfc/reference/exception-processing.md)或者參閱本文 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
 若要攔截特定例外狀況，請使用適當的衍生類別。  若要攔截例外狀況的所有型別，請使用 `CException`，然後使用 [CObject::IsKindOf](../Topic/CObject::IsKindOf.md)`CException`在衍生類別中區分。  請注意 `CObject::IsKindOf` 只適用於類別的宣告 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md) 巨集，以使用動態型別檢查。  任何 `CException`\-您建立的衍生類別都應該使用 `IMPLEMENT_DYNAMIC` 巨集，則也是。  
  
 您可以與例外狀況有關的詳細資料會向使用者報告藉由呼叫 [GetErrorMessage](../Topic/CFileException::GetErrorMessage.md) 或 [ReportError](../Topic/CException::ReportError.md)，以及任何 `CException` 的衍生類別所需的兩個成員函式。  
  
 如果例外狀況是由其中一個巨集 `CException` 攔截，會自動刪除物件;請勿刪除自己。  您可以使用 **catch** 關鍵字，如果偵測到例外狀況，它不會自動刪除。  何時參閱本文 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md) 如需刪除 exeption 物件的詳細資訊。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CException`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [例外狀況處理](../../mfc/reference/exception-processing.md)   
 [如何?:建立自己的自訂例外狀況類別?](http://go.microsoft.com/fwlink/?LinkId=128045)