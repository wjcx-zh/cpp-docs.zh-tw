---
title: "屬性頁 (MFC) | Microsoft Docs"
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
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 中的屬性頁資料傳輸函式"
  - "屬性頁, 全域 MFC 函式"
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
caps.latest.revision: 14
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 屬性頁 (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

屬性頁可以支援根據對話資料交換的一組資料配置機制顯示目前值在自訂的特定 OLE automation 控制項檢視和編輯的屬性，圖形介面 \(Dialog Data Exchange，DDX\)。  
  
 這個資料配置機制對應屬性頁控制對 OLE automation 控制項的個別屬性。  控制項屬性的值會反映屬性頁控制項的狀態或內容。  屬性頁控制項和屬性之間的對應是由 **DDP\_** 函式呼叫中指定屬性頁的 `DoDataExchange` 成員函式。  下列是 **DDP\_** 清單函式使用控制項，則屬性頁交換資料輸入:  
  
### 屬性頁資料傳輸  
  
|||  
|-|-|  
|[DDP\_CBIndex](../Topic/DDP_CBIndex.md)|連結下拉式方塊中選取有控制項屬性的字串的索引。|  
|[DDP\_CBString](../Topic/DDP_CBString.md)|連結下拉式方塊中選取有控制項屬性的字串的索引。  選取的字串可能以字母開頭和屬性值相同，但不需要完全相符。|  
|[DDP\_CBStringExact](../Topic/DDP_CBStringExact.md)|連結下拉式方塊中選取有控制項屬性的字串的索引。  選取的資料和屬性的字串值必須完全相符。|  
|[DDP\_Check](../Topic/DDP_Check.md)|與控制項的屬性連結控制項的屬性頁中的核取方塊。|  
|[DDP\_LBIndex](../Topic/DDP_LBIndex.md)|連結清單方塊中選取有控制項屬性的字串的索引。|  
|[DDP\_LBString](../Topic/DDP_LBString.md)|連結在清單方塊中選取有控制項屬性的索引的字串。  選取的字串可能以字母開頭和屬性值相同，但不需要完全相符。|  
|[DDP\_LBStringExact](../Topic/DDP_LBStringExact.md)|連結在清單方塊中選取有控制項屬性的索引的字串。  選取的資料和屬性的字串值必須完全相符。|  
|[DDP\_PostProcessing](../Topic/DDP_PostProcessing.md)|從您的控制項完成屬性值傳輸。|  
|[DDP\_Radio](../Topic/DDP_Radio.md)|與控制項的屬性連結控制項的屬性頁中的選項按鈕群組。|  
|[DDP\_Text](../Topic/DDP_Text.md)|與控制項的屬性連結控制項的屬性頁中的控制項。  這個函式處理屬性的幾種不同的型別，例如 **double**和 **short**和 **long**、 `BSTR`。|  
  
 如需 `DoDataExchange` 函式和屬性頁的詳細資訊，請參閱本文件的 [ActiveX 控制項:屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。  
  
 下列是用於的巨集清單建立和管理 OLE automation 控制項的屬性頁:  
  
### 屬性頁  
  
|||  
|-|-|  
|[BEGIN\_PROPPAGEIDS](../Topic/BEGIN_PROPPAGEIDS.md)|啟動屬性頁 ID 清單。|  
|[END\_PROPPAGEIDS](../Topic/END_PROPPAGEIDS.md)|結束屬性頁 ID 清單。|  
|[PROPPAGEID](../Topic/PROPPAGEID.md)|宣告控制項類別的屬性頁。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)