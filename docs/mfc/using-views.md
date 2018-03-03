---
title: "使用 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99493657313d480559d232bf9033dfb7a7a585c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-views"></a>使用檢視
檢視的責任是以圖形方式顯示給使用者的文件的資料，以及為接受和解譯使用者輸入為文件上的作業。 您在撰寫您的檢視類別的工作如下：  
  
-   撰寫您的檢視類別[OnDraw](../mfc/reference/cview-class.md#ondraw)成員函式，以呈現文件的資料。  
  
-   連接適當的 Windows 訊息和使用者介面物件，例如功能表項目檢視類別中的訊息處理常式成員函式。  
  
-   實作這些處理常式來解譯使用者輸入。  
  
 此外，您可能需要覆寫其他`CView`衍生的檢視類別中的成員函式。 特別是，您可能想要覆寫[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)檢視執行特殊的初始化和[OnUpdate](../mfc/reference/cview-class.md#onupdate)執行檢視重繪本身之前，只需要任何特殊處理。 對於多頁文件，您也必須覆寫[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)初始化要列印的頁面及其他資訊的數字與 [列印] 對話方塊。 如需有關覆寫`CView`成員函式，請參閱類別[CView](../mfc/reference/cview-class.md)中*MFC 參考*。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [MFC 中的可用衍生的檢視類別](../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [在檢視中繪圖](../mfc/drawing-in-a-view.md)  
  
-   [透過檢視解譯使用者輸入](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [檢視在列印中的角色](../mfc/role-of-the-view-in-printing.md)  
  
-   [捲動和縮放檢視](../mfc/scrolling-and-scaling-views.md)  
  
-   [初始化和清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
## <a name="see-also"></a>請參閱  
 [文件/檢視架構](../mfc/document-view-architecture.md)   
 [CFormView 類別](../mfc/reference/cformview-class.md)   
 [資料錄檢視 （MFC 資料存取）](../data/record-views-mfc-data-access.md)   
 [略過序列化機制](../mfc/bypassing-the-serialization-mechanism.md)

