---
title: "拖放：自訂 | Microsoft Docs"
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
  - "拖放, 呼叫 DoDragDrop"
  - "拖放, COleDataSource 物件"
  - "拖放, 自訂行為"
  - "拖放, 在非 OLE 應用程式中實作"
  - "OLE 拖放, 自訂行為"
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 拖放：自訂
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

拖放功能的預設實作會提供大部分應用程式而言已經足夠。  不過，某些應用程式可能需要變更這個標準行為。  本文說明的必要步驟變更這些預設值。  此外，您可以使用這項技術建立不支援複合文件在置放來源的應用程式。  
  
 如果您自訂標準 OLE 拖放行為，這可能是有非 OLE 應用程式，您必須建立 `COleDataSource` 物件包含資料。  當使用者開始拖放作業時，您的程式碼應該呼叫此物件的 `DoDragDrop` 函式而不是從其他類別支援拖放作業。  
  
 或者，您可以建立 `COleDropSource` 物件控制置放和根據您要變更的行為型別覆寫這些函式。  這個置放來源物件傳遞至 `COleDataSource::DoDragDrop` 變更這些函式預設行為。  這些不同的選項讓您方式擁有更多的彈性支援在應用程式的拖放作業。  如需資料來源的詳細資訊，請參閱本文件的 [資料物件和資料來源 \(Object Linking and Embedding，OLE\)](../mfc/data-objects-and-data-sources-ole.md)。  
  
 您可以覆寫下列函式自訂拖放作業:  
  
|覆寫|自訂|  
|--------|--------|  
|`OnBeginDrag`|如何在呼叫 `DoDragDrop`之後啟始拖曳。|  
|`GiveFeedback`|視覺化回應，例如游標外觀，不同的結果。|  
|`QueryContinueDrag`|拖放作業的結束。  這個函式可讓您在拖曳作業期間檢查修飾詞按鍵狀態。|  
  
## 請參閱  
 [拖放 \(OLE\)](../mfc/drag-and-drop-ole.md)   
 [COleDropSource Class](../mfc/reference/coledropsource-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)