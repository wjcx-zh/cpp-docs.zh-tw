---
title: 列印 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7df782e3c30b9120fe7eb6728f1b622750d160f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="printing"></a>列印
Microsoft Windows 實作與裝置無關的顯示。 在 MFC 中，這表示相同的繪製呼叫，在`OnDraw`負責繪圖和其他裝置，例如印表機上顯示您的檢視類別成員函式。 預覽列印，目標裝置是模擬的印表機輸出到顯示器。  
  
##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> 您在列印架構的角色與角色  
 您的檢視類別具有下列責任：  
  
-   告知架構文件中有多少頁數。  
  
-   當系統要求您列印指定的頁面時，繪製文件的部分。  
  
-   配置及取消配置任何字型或其他列印所需的圖形裝置介面 (GDI) 資源。  
  
-   必要時，傳送任何逸出，例如列印指定的頁面之前變更印表機模式，來變更每個頁面為基礎的列印方向所需的程式碼。  
  
 架構的責任是，如下所示：  
  
-   顯示**列印** 對話方塊。  
  
-   建立[CDC](../mfc/reference/cdc-class.md)印表機的物件。  
  
-   呼叫[Cdc](../mfc/reference/cdc-class.md#startdoc)和[EndDoc](../mfc/reference/cdc-class.md#enddoc)的成員函式`CDC`物件。  
  
-   重複呼叫[StartPage](../mfc/reference/cdc-class.md#startpage)成員函式`CDC`物件時，通知檢視類別應列印哪些頁面，並呼叫[EndPage](../mfc/reference/cdc-class.md#endpage)成員函式`CDC`物件。  
  
-   呼叫可覆寫的函式在檢視中，在適當的時間。  
  
 下列文章中討論的架構如何支援列印和預覽列印：  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [如何完成預設列印](../mfc/how-default-printing-is-done.md)  
  
-   [多頁文件](../mfc/multipage-documents.md)  
  
-   [頁首和頁尾](../mfc/headers-and-footers.md)  
  
-   [列印配置 GDI 資源](../mfc/allocating-gdi-resources.md)  
  
-   [預覽列印](../mfc/print-preview-architecture.md)  
  
## <a name="see-also"></a>另請參閱  
 [列印和預覽列印](../mfc/printing-and-print-preview.md)

