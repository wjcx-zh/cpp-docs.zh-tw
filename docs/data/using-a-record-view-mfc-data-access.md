---
title: "使用記錄檢視 (MFC 資料存取) | Microsoft Docs"
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
  - "資料錄檢視, 自訂預設程式碼"
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用記錄檢視 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題說明通常如何自訂精靈為您撰寫的資料錄檢視的預設程式碼。  一般而言，您會想要使用[篩選條件](../data/odbc/recordset-filtering-records-odbc.md)或[參數](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)來限制資料錄選取，也或許是想要[排序](../data/odbc/recordset-sorting-records-odbc.md)資料錄、自訂 SQL 陳述式。  
  
 這項資訊適用於 [CRecordView](../mfc/reference/crecordview-class.md) \(ODBC\) 和[CDaoRecordView](../mfc/reference/cdaorecordview-class.md) \(DAO\) 兩者。  
  
 使用 `CRecordView` 或 `CDaoRecordView` 與使用 [CFormView](../mfc/reference/cformview-class.md) 非常類似。  基本方法是使用資料錄檢視顯示甚或更新單一資料錄集的記錄。  此外，您可能也會想要使用其他資料錄集，如[資料錄檢視：以第二個資料錄集填入清單方塊](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)中所討論。  
  
## 請參閱  
 [記錄檢視 \(MFC 資料存取\)](../data/record-views-mfc-data-access.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)