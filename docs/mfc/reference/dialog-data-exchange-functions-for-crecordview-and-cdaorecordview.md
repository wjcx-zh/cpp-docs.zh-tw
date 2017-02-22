---
title: "CRecordView 和 CDaoRecordView 的對話方塊資料交換函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], 對話方塊資料交換 (DDX) 支援"
  - "資料庫 [C++], 對話方塊資料交換 (DDX) 支援"
  - "DDX (對話方塊資料交換) [C++], 資料庫支援"
  - "DDX (對話方塊資料交換) [C++], 函式"
  - "DDX_Field 函式"
  - "ODBC [C++], 對話方塊資料交換 (DDX) 支援"
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CRecordView 和 CDaoRecordView 的對話方塊資料交換函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題列出 DDX\_Field 函式在 [CRecordset](../../mfc/reference/crecordset-class.md) 和 [CRecordView](../../mfc/reference/crecordview-class.md) 表單間交換資料或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 和 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 表單。  
  
> [!NOTE]
>  DDX\_Field 函式與 DDX 函式它們與控制項交換資料的格式。  但是，不同於 DDX，它們與檢視的關聯資料錄集物件的欄位交換資料而不是使用資料錄檢視的欄位。  如需詳細資訊，請參閱 `CRecordView` 和`CDaoRecordView`類別。  
  
### DDX\_Field 函式  
  
|||  
|-|-|  
|[DDX\_FieldCBIndex](../Topic/DDX_FieldCBIndex.md)|傳輸資料錄集欄位資料成員和目前選取範圍的索引在下拉式方塊在 [CRecordView](../../mfc/reference/crecordview-class.md) 或 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)的整數資料。|  
|[DDX\_FieldCBString](../Topic/DDX_FieldCBString.md)|傳輸資料錄集欄位資料成員和下拉式方塊的編輯控制項在 `CRecordView` 或 `CDaoRecordView`的 `CString` 資料。  當從資料錄集的資料加入至控制項，這個函式選取從在指定字串中字元開頭的下拉式方塊中的項目。|  
|[DDX\_FieldCBStringExact](../Topic/DDX_FieldCBStringExact.md)|傳輸資料錄集欄位資料成員和下拉式方塊的編輯控制項在 `CRecordView` 或 `CDaoRecordView`的 `CString` 資料。  當從資料錄集的資料加入至控制項，這個函式選取完全符合指定字串的下拉式方塊中的項目。|  
|[DDX\_FieldCheck](../Topic/DDX_FieldCheck.md)|在資料錄集欄位資料成員和一個核取方塊在 `CRecordView` 或 `CDaoRecordView`傳輸布林值資料。|  
|[DDX\_FieldLBIndex](../Topic/DDX_FieldLBIndex.md)|傳輸資料錄集欄位資料成員和目前選取範圍的索引在清單方塊在 `CRecordView` 或 `CDaoRecordView`的整數資料。|  
|[DDX\_FieldLBString](../Topic/DDX_FieldLBString.md)|處理 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 資料傳輸在清單方塊控制項和資料錄集的欄位資料成員的。  當從資料錄集的資料加入至控制項，這個函式選取從在指定字串中字元開頭的清單方塊中的項目。|  
|[DDX\_FieldLBStringExact](../Topic/DDX_FieldLBStringExact.md)|處理 `CString` 資料傳輸在清單方塊控制項和資料錄集的欄位資料成員的。  當從資料錄集的資料加入至控制項，這個函式選取完全符合指定字串的第一個項目。|  
|[DDX\_FieldRadio](../Topic/DDX_FieldRadio.md)|傳輸資料錄集欄位資料成員和選項按鈕群組在 `CRecordView` 或 `CDaoRecordView`的整數資料。|  
|[DDX\_FieldScroll](../Topic/DDX_FieldScroll.md)|設定或取得捲軸控制項的捲動位置在 `CRecordView` 或 `CDaoRecordView`。  從 [DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md) 函式的呼叫。|  
|[DDX\_FieldText](../Topic/DDX_FieldText.md)|多載版本為傳輸 `int`、 **UINT**、 **long**、 `DWORD`、 [CString](../../atl-mfc-shared/reference/cstringt-class.md)、 **float**、 **double**、 **short**、 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和 [COleCurrency](../../mfc/reference/colecurrency-class.md) 資料可以在資料錄集欄位資料成員和在 `CRecordView` 上的編輯方塊或 `CDaoRecordView`中的項目。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)