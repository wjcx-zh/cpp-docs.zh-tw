---
title: "顯示和操作表單中的資料 | Microsoft Docs"
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
  - "資料 [MFC]"
  - "資料 [MFC], 在表單中顯示"
  - "顯示資料 [C++], 表單"
  - "表單 [C++], 顯示資料"
  - "ODBC [C++], 表單"
  - "資料錄檢視 [C++], 顯示資料"
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 顯示和操作表單中的資料
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

許多資料存取應用程式會在表單欄位中選取資料和顯示資料。  [CRecordView](../../mfc/reference/crecordview-class.md) 資料庫類別可提供您直接連接到資料錄集物件的 [CFormView](../../mfc/reference/cformview-class.md) 物件。  資料錄檢視會使用[對話資料交換 \(DDX\)](../../mfc/dialog-data-exchange-and-validation.md)，將目前資料錄的欄位值從資料錄集移動至表單的控制項，並將更新過的資訊移回資料錄集。  資料錄集會依序地使用資料錄欄位交換 \(RFX\)，來移動其欄位資料成員之間的值，和資料來源中的相關資料表資料行。  
  
 您可以使用 \[MFC 應用程式精靈\] 或是 \[加入類別\] \(詳述於[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)\)，以建立該檢視類別，和其聯合的關聯資料錄集類別。  
  
 資料錄檢視和其資料錄集會在您關閉文件時終止。  如需資料錄檢視的詳細資訊，請參閱[資料錄檢視](../../data/record-views-mfc-data-access.md)。  如需 RFX 的詳細資訊，請參閱[資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)。  
  
## 請參閱  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)