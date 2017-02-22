---
title: "CDaoException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoException class"
  - "集合, DAO 錯誤"
  - "DAO (資料存取物件), 例外狀況"
  - "錯誤 [C++], DAO"
  - "Errors collection, DAO"
  - "例外狀況, in MFC DAO classes"
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDaoException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示顯示從 MFC 資料庫類別的例外狀況架構的資料存取物件 \(DAO\)。  
  
## 語法  
  
```  
class CDaoException : public CException  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDaoException::CDaoException](../Topic/CDaoException::CDaoException.md)|建構 `CDaoException` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDaoException::GetErrorCount](../Topic/CDaoException::GetErrorCount.md)|傳回錯誤數目資料庫引擎的錯誤集合的。|  
|[CDaoException::GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md)|會傳回有關特定錯誤之物件的錯誤訊息在錯誤集合。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDaoException::m\_nAfxDaoError](../Topic/CDaoException::m_nAfxDaoError.md)|在 MFC DAO 類別包含所有錯誤的其中一個延伸錯誤碼。|  
|[CDaoException::m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md)|對含有 DAO 錯誤物件資訊的 [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) 物件的指標。|  
|[CDaoException::m\_scode](../Topic/CDaoException::m_scode.md)|[SCODE](../Topic/CDaoException::m_scode.md) 值與錯誤相關聯的。|  
  
## 備註  
 類別包含可用於判斷例外狀況原因的公用資料成員。  `CDaoException` 物件由 DAO 資料庫類別的成員函式建構並擲回。  
  
> [!NOTE]
>  DAO 資料庫類別會根據 Open 開放式資料庫連接的 MFC 資料庫類別本身不同 \(ODBC\)。  所有 DAO 資料庫類別名稱中有「CDao」前置詞。  您仍然可以存取使用 DAO 類別的 ODBC 資料來源。  一般而言，根據的 MFC DAO 類別比 ODBC 架構的 MFC 類別功能;以 DAO 類別的類別可以存取資料，包括透過 ODBC 驅動程式，將它們自己的資料庫引擎。  DAO 架構的類別會透過類別也支援資料定義語言 \(DDL\) \(DDL\) 作業，例如，加入資料表，而不需要直接呼叫 DAO。  如需 ODBC 類別所擲回的例外狀況的詳細資訊，請參閱 [CDBException](../../mfc/reference/cdbexception-class.md)。  
  
 在 [catch](../Topic/CATCH.md) 運算式的範圍內，您可以存取例外狀況物件。  您也可以擲回從自己的程式碼的 `CDaoException` 物件與 [AfxThrowDaoException](../Topic/AfxThrowDaoException.md) 全域函式。  
  
 在 MFC DAO，所有錯誤表示為例外狀況，型別 `CDaoException`。  當您擲回型別的例外狀況時，您可以使用 `CDaoException` 成員函式在資料庫引擎的錯誤集合中的所有 DAO Error 物件擷取資訊。  當每個錯誤，一個或多個錯誤物件在錯誤的集合中。  \(集合通常只包含錯誤物件;如果您是使用 ODBC 資料來源，您便可以取得多個錯誤物件\)。當其他 DAO 作業產生錯誤時，會清除集合，錯誤，而且新的錯誤物件在錯誤的集合中。  不會產生錯誤的 DAO 作業並不會影響錯誤集合的效果。  
  
 如需 DAO 錯誤程式碼，請參閱檔案 DAOERR.H。  如需相關資訊，請參閱本主題稍後的「可截獲的資料存取錯誤《DAO 說明。  
  
 如需一般，例外處理的詳細資訊 `CDaoException` 物件或相關資訊，請參閱 Microsoft 知識庫文件 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md) 和 [例外狀況:資料庫例外狀況。](../../mfc/exceptions-database-exceptions.md)。  第二個文章包含說明例外狀況處理 DAO 的範例程式碼。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)