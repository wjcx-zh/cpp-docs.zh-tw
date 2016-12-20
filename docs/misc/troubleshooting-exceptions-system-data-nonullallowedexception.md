---
title: "疑難排解例外狀況：System.Data.NoNullAllowedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "NoNullAllowedException 類別"
ms.assetid: 1ab87572-007f-4b84-bb13-c3626e7f89cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.NoNullAllowedException
嘗試將 null 值插入資料行，而此資料行的 <xref:System.Data.NoNullAllowedException> 設定為 <xref:System.Data.DataColumn.AllowDBNull%2A> 時，就會擲回 `false` 例外狀況。  
  
## 相關秘訣  
 **將值加入至資料行之前，先檢查該值是否為 DBNull。**  
 如果 <xref:System.Data.DataColumn.AllowDBNull%2A> 設定為 `false`，將無法插入 null 值。 如需詳細資訊，請參閱<xref:System.DBNull>。  
  
 **將 AllowDBNull 設定為 true。**  
 將這個屬性設定為 `true` 可讓您插入 null 值。 如需詳細資訊，請參閱<xref:System.Data.DataColumn.AllowDBNull%2A>。  
  
## 備註  
 如果您在資料表單上使用巡覽按鈕瀏覽資料庫資料表的記錄時，可能會擲回此含有額外資訊的例外狀況：「資料行 'Column' 不允許 null」。 這個行為發生的原因，是因為在資料表單精靈 \(Data Form Wizard\) 中未選取資料庫資料表的主索引鍵或 \[非 NULL\] 資料行。 當您建立資料表單，而未在資料表單精靈中選取資料庫的主索引鍵或 \[非 NULL\] 資料行時，就不會停用 \[**加入 \- 建立新的記錄**\] 選項。 要解決這個問題，請在加入資料表單時，使用資料表單精靈選取下列已選取資料表的資料行：主索引鍵資料行以及不允許 NULL 的資料行。  
  
## 請參閱  
 <xref:System.Data.NoNullAllowedException>   
 <xref:System.Data.DataRowCollection.Add%2A>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 <xref:System.Data.DataTable.LoadDataRow%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)