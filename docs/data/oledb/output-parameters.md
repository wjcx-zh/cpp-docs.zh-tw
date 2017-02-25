---
title: "輸出參數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "程序呼叫"
  - "程序呼叫, 預存程序"
  - "預存程序, 呼叫"
  - "預存程序, 參數"
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 輸出參數
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫一個預存程序類似於叫用一個 SQL 命令。  兩者的主要差異是，預存程序會使用輸出參數 \(或 "outparameters"\) 和傳回值。  
  
 在下列預存程序中，第一個 '?' 是傳回值 \(phone\)，第二個 '?' 輸入參數 \(name\)：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  
  
 您可以在參數對應中指定輸入和輸出參數：  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter  
END_PARAM_MAP()  
```  
  
 您的應用程式必須處理由預存程序傳回的輸出。  不同的 OLE DB 提供者在結果處理時期，會在不同時間傳回輸出參數和傳回值。  例如，Microsoft OLE DB Provider for SQL Server \(SQLOLEDB\) 會一直到消費者擷取或取消預存程序傳回的結果集時，才提供輸出參數和傳回碼。  輸出會由來自伺服器的最後一個 TDS 封包傳回。  
  
## 資料列數  
 如果您使用 OLE DB 消費者樣板執行含有 outparameters 的預存程序，就要等到關閉該資料列集後才設定資料列數。  
  
 例如，請參考一個具資料列集和輸出參數的預存程序：  
  
```  
create procedure sp_test  
   @_rowcount integer output  
as  
   select top 50 * from test  
   @_rowcount = @@rowcount  
return 0  
```  
  
 @\_rowcount outparameter 會報告實際上有多少資料列從測試資料表傳回。  然而，這個預存程序將資料列的數目限制在最多 50 個。  例如，如果測試中有 100 個資料列，資料列數便會是 50 \(因為這段程式碼只會擷取前面的 50 個資料列\)。  如果資料表中只有 30 個資料列，則資料列數會是 30。  您必須在擷取資料表的值之前，呼叫 **Close** 或 **CloseAll** 來填入 outparameter。  
  
## 請參閱  
 [使用預存程序](../../data/oledb/using-stored-procedures.md)