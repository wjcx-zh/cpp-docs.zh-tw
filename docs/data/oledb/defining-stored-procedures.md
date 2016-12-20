---
title: "定義預存程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB, 預存程序"
  - "預存程序, 定義"
  - "預存程序, OLE DB"
  - "預存程序, 語法"
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 定義預存程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您必須在呼叫預存程序之前，先使用 [DEFINE\_COMMAND](../../data/oledb/define-command.md) 巨集定義它。  當您定義命令時，請以問號 \(?\) 做為參數標記來代表參數：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 請注意，這個主題的程式碼範例所使用的語法 \(例如，括號等用法\) 是 SQL Server 專用的。  您在預存程序中所使用的語法可能會根據使用的提供者而有所不同。  
  
 接著，在參數對應中指定您用於命令的參數，並依照參數在命令中出現的順序列出：  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 先前的範例會在執行時定義預存程序。  通常，為了有效重複使用程式碼，資料庫會包含一組名為 "Sales by Year" 或 "dt\_adduserobject" 的預先定義的預存程序。您可以使用 SQL Server Enterprise Manager 檢視它們的定義。  您可以依照下列方式來呼叫它們 \('?' 參數的位置會依不同的預存程序介面而有所差異\)：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 接著，宣告命令類別：  
  
```  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor> >  
```  
  
 最後，請依照下列方式，在 `OpenRowset` 中呼叫預存程序：  
  
```  
CSession m_session;  
HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor> >::Open(m_session);  
}  
```  
  
 同時請注意，您可以依照下列方式，使用資料庫屬性 [db\_command](../../windows/db-command.md) 定義預存程序：  
  
```  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## 請參閱  
 [使用預存程序](../../data/oledb/using-stored-procedures.md)