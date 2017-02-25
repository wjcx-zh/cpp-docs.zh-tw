---
title: "CCommand::GetNextResult | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CCommand::GetNextResult"
  - "CCommand::GetNextResult"
  - "GetNextResult"
  - "CCommand.GetNextResult"
  - "ATL.CCommand.GetNextResult"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetNextResult 方法"
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CCommand::GetNextResult
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果有可用，擷取的下一個結果集。  
  
## 語法  
  
```  
  
      HRESULT GetNextResult(  
   DBROWCOUNT* pulRowsAffected,  
   bool bBind = true   
) throw( );  
```  
  
#### 參數  
 *pulRowsAffected*  
 \[in\/out\]in\] 命令影響的計數資料行中傳回的記憶體指標。  
  
 `bBind`  
 \[in\] 指定是否在執行之後自動繫結至命令。  預設值為 **true**，導致命令自動繫結。  對 **false** 的設定 `bBind` 以防止命令的自動繫結，讓您可以手動繫結。\(手動繫結是特殊的感興趣 OLAP 使用者\)。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 如果結果集先前已擷取，前一個結果集的此函式版本和解除繫結資料行。  如果 `bBind` 是 **true**，它會繫結至新的資料行。  
  
 您應該呼叫這個函式時，才可以藉由設定 `CCommand` 樣板參數指定了多個結果 *TMultiple\=*`CMultipleResults`。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)