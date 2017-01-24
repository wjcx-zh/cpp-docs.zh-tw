---
title: "CRowset::FindNextRow | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset.FindNextRow"
  - "CRowset<TAccessor>.FindNextRow"
  - "ATL::CRowset::FindNextRow"
  - "CRowset::FindNextRow"
  - "CRowset<TAccessor>::FindNextRow"
  - "CRowset.FindNextRow"
  - "ATL.CRowset<TAccessor>.FindNextRow"
  - "ATL::CRowset<TAccessor>::FindNextRow"
  - "FindNextRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FindNextRow 方法"
ms.assetid: 36484df9-3625-4f15-bf69-db73a8d91c55
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::FindNextRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尋找在指定的書籤後下一個符合的資料列。  
  
## 語法  
  
```  
  
      HRESULT FindNextRow(   
   DBCOMPAREOP op,   
   BYTE* pData,   
   DBTYPE wType,   
   DBLENGTH nLength,   
   BYTE bPrecision,   
   BYTE bScale,   
   BOOL bSkipCurrent = TRUE,   
   CBookmarkBase* pBookmark = NULL    
) throw( );  
```  
  
#### 參數  
 `op`  
 \[in\] 要在比較資料行值使用的作業。  關於值，請參閱 [IRowsetFind::FindNextRow](https://msdn.microsoft.com/en-us/library/ms723091.aspx)。  
  
 `pData`  
 \[in\] 要比對之值的指標。  
  
 `wType`  
 \[in\] 表示部分緩衝區值的資料型別。  如需型別指標的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中 *OLE DB 程式設計人員參考資訊* 的 [資料型別](https://msdn.microsoft.com/en-us/library/ms723969.aspx)。  
  
 `nLength`  
 \[in\] 為資料值配置的消費者資料結構之長度 \(以位元組為單位\)。  如需詳細資訊，請參閱 *OLE DB 程式設計人員參考資訊* 中 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx) 的 **cbMaxLen** 說明。  
  
 `bPrecision`  
 \[in\] 取得資料時使用的最大精確度。  只有在 `wType` 為 `DBTYPE_NUMERIC` 時使用。  如需詳細資訊，請參閱 *OLE DB 程式設計人員參考資訊* 的 [包含 DBTYPE\_NUMERIC 或 DBTYPE\_DECIMAL 的轉換](https://msdn.microsoft.com/en-us/library/ms719714.aspx)。  
  
 `bScale`  
 \[in\] 取得資料時使用的功能。  只有在 `wType` 為 `DBTYPE_NUMERIC` 或 **DBTYPE\_DECIMAL** 時使用。  如需詳細資訊，請參閱 *OLE DB 程式設計人員參考資訊* 的 [包含 DBTYPE\_NUMERIC 或 DBTYPE\_DECIMAL 的轉換](https://msdn.microsoft.com/en-us/library/ms719714.aspx)。  
  
 *bSkipCurrent*  
 \[in\] 書籤中開始搜尋的資料行編號。  
  
 `pBookmark`  
 \[in\] 開始搜尋的書籤位置。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法要求選擇性的 **IRowsetFind** 介面，此介面可能不是所有提供者都支援；如果是這種情況，方法會傳回 **E\_NOINTERFACE**。  您也必須在對資料表或是包含資料列集的命令呼叫 **Open** 之前，設定 **DBPROP\_IRowsetFind** 為 `VARIANT_TRUE`。  
  
 如需在消費者內使用書籤的資訊，請參閱 [使用書籤](../../data/oledb/using-bookmarks.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [DBBINDING Structures](https://msdn.microsoft.com/en-us/library/ms716845.aspx)