---
title: "使用手動存取子 | Microsoft Docs"
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
  - "存取子 [C++], 手動"
  - "命令處理, OLE DB 樣板"
  - "手動存取子"
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用手動存取子
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在處理未知命令時，要完成四件事情：  
  
-   決定參數  
  
-   執行命令  
  
-   決定輸出資料行  
  
-   查看是否有多個傳回資料列集  
  
 若要使用 OLE DB 消費者樣板達成這個目的，請使用 `CManualAccessor` 類別並遵循這些步驟：  
  
1.  將 `CManualAccessor` 當做範例參數以開啟 `CCommand` 物件。  
  
    ```  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  查詢 **IDBSchemaRowset** 介面的工作階段，並使用程序參數資料列集。  如果無法使用 **IDBSchemaRowset** 介面，請查詢 `ICommandWithParameters` 介面。  呼叫 `GetParameterInfo` 以取得資訊。  如果兩個介面都無法使用，您可以假設沒有參數存在。  
  
3.  為每個參數呼叫 `AddParameterEntry` 以加入參數並設定他們。  
  
4.  開啟資料列集但是將繫結參數設成 **false**。  
  
5.  呼叫 `GetColumnInfo` 以擷取輸出資料行。  使用 `AddBindEntry` 將輸出資料行加入至繫結。  
  
6.  呼叫 `GetNextResult` 以決定是否有更多可使用的資料列集。  重複步驟 2 到 5。  
  
 如需手動存取子的範例，請參閱 [DBVIEWER](http://msdn.microsoft.com/zh-tw/07620f99-c347-4d09-9ebc-2459e8049832) 範例中的 **CDBListView::CallProcedure**。  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)