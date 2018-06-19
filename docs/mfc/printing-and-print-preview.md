---
title: 列印和預覽列印 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a26bac196dbddc6c05df5850225d05f432bc566
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346252"
---
# <a name="printing-and-print-preview"></a>列印和預覽列印
MFC 透過類別的程式的文件支援列印和預覽列印[CView](../mfc/reference/cview-class.md)。 基本列印和預覽列印，只是覆寫檢視類別的[OnDraw](../mfc/reference/cview-class.md#ondraw)成員函式，您必須這麼做。 該函式可以繪製畫面上，印表機裝置內容中，實際的印表機上的檢視，或裝置內容，用於模擬您在螢幕上的印表機。  
  
 您也可以加入程式碼來管理多頁文件列印和預覽列印的文件重新編頁，並為其新增頁首和頁尾。  
  
 此系列文章說明如何實作列印在 Microsoft Foundation 類別庫 (MFC)，以及如何運用內建架構的列印架構。 文件也會說明 MFC 如何支援預覽列印功能的簡單實作，以及如何使用及修改該功能。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [列印](../mfc/printing.md)  
  
-   [預覽列印架構](../mfc/print-preview-architecture.md)  
  
-   [範例](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)
