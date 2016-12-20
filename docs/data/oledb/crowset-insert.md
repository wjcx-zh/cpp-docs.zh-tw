---
title: "CRowset::Insert | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset<TAccessor>.Insert"
  - "CRowset.Insert"
  - "CRowset<TAccessor>.Insert"
  - "CRowset<TAccessor>::Insert"
  - "ATL::CRowset<TAccessor>::Insert"
  - "ATL.CRowset.Insert"
  - "CRowset::Insert"
  - "ATL::CRowset::Insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Insert 方法"
ms.assetid: 6a64a1c3-10ac-4296-8685-0fd6fe63a13b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Insert
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用存取的資料建立和初始化一個新的資料列。  
  
## 語法  
  
```  
  
      HRESULT Insert(   
   int nAccessor = 0,   
   bool bGetHRow = false    
) throw( );  
```  
  
#### 參數  
 `nAccessor`  
 \[in\]使用存取子的數字為插入資料。  
  
 *bGetHRow*  
 \[in\]表示是否已擷取插入資料列的控制代碼。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法要求選擇性 `IRowsetChange` 介面，可能不是所有提供者都支援;如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  在對資料表或是包含資料列集的命令呼叫 **Open** 之前您也必須設定 **DBPROP\_IRowsetChange** 到 `VARIANT_TRUE`。  
  
 如果出現一個或多個資料行無法寫入的情形，插入便可能會失敗。  請修改您的資料指標 \(Cursor\) 對應以修正這個問題。  
  
## 範例  
 下列範例會在該資料列集顯示如何存取資料來源並將資料列集然後插入字串資料表。  
  
 首先，插入新的 ATL 物件至專案以建立資料表類別。  例如，請以滑鼠右鍵按一下工作區窗格的專案並選擇 **New ATL 物件**。  從 **Data Access** 分類選取 **Consumer**。  建立**Table**型別的消費者物件。\(選取 **Table** 以建立資料列集直接從資料表；選取 **Command** 透過 SQL 命令建立資料列集\)。選取資料來源，指定資料表存取該資料來源。  如果您呼叫您的消費者物件 **CCustomerTable**，您就可以實作自己的插入程式碼如下所示:  
  
 [!code-cpp[NVC_OLEDB_Consumer#10](../../data/oledb/codesnippet/CPP/crowset-insert_1.cpp)]  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)