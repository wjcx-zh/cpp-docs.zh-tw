---
title: "CDBException Class | Microsoft Docs"
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
  - "CDBException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBException class"
  - "database exceptions [C++]"
  - "錯誤 [C++], 資料庫"
  - "exceptions [C++], 資料庫"
  - "ODBC 類別 [C++], 例外狀況"
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
caps.latest.revision: 23
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示會顯示從資料庫類別的例外狀況。  
  
## 語法  
  
```  
  
class CDBException : public CException  
  
```  
  
## Members  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDBException::m\_nRetCode](../Topic/CDBException::m_nRetCode.md)|包含一個開放式資料庫連接 \(Open Database Connectivity，ODBC\) 傳回碼，型別 **RETCODE**。|  
|[CDBException::m\_strError](../Topic/CDBException::m_strError.md)|包含說明錯誤的英數字元的用語的字串。|  
|[CDBException::m\_strStateNativeOrigin](../Topic/CDBException::m_strStateNativeOrigin.md)|包含說明錯誤的字串會根據 ODBC 傳回的錯誤碼。|  
  
## 備註  
 類別包含可用於判斷造成例外狀況的原因或顯示描述例外狀況的文字訊息的兩個公用資料成員。  `CDBException` 物件由資料庫類別的成員函式建構並擲回。  
  
> [!NOTE]
>  這個類別是其中一個 MFC 的開放式資料庫連接 \(Open Database Connectivity，ODBC\) 類別。  如果您使用較新的資料存取物件 \(DAO\) 類別，使用 [CDaoException](../../mfc/reference/cdaoexception-class.md) 。  所有 DAO 類別名稱中有「CDao」做為前置字元。  如需詳細資訊，請參閱本文 [概觀:資料庫程式開發](../../data/data-access-programming-mfc-atl.md)。  
  
 例外狀況是異常執行包含在控制項外部程序的情況下條件，例如資料來源或網路 I\/O 錯誤。  您可以在執行您的程式一般路徑可能會預期看到的錯誤通常不會被視為例外狀況。  
  
 在 **CATCH** 運算式的範圍內，您可以存取這些物件。  您也可以擲回從自己的程式碼的 `CDBException` 物件與 `AfxThrowDBException` 全域函式。  
  
 如需一般，例外處理的詳細資訊 `CDBException` 物件或相關資訊，請參閱 Microsoft 知識庫文件 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md) 和 [例外狀況:資料庫例外狀況。](../../mfc/exceptions-database-exceptions.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDBException`  
  
## 需求  
 **Header:** afxdb.h  
  
## 請參閱  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)   
 [AfxThrowDBException](../Topic/AfxThrowDBException.md)   
 [CRecordset::Update](../Topic/CRecordset::Update.md)   
 [CRecordset::Delete](../Topic/CRecordset::Delete.md)   
 [CException Class](../../mfc/reference/cexception-class.md)