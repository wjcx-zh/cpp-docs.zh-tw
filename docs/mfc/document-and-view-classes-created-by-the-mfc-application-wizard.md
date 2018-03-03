---
title: "文件和檢視類別，MFC 應用程式精靈建立 |Microsoft 文件"
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
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cddf8b72e9927a298cbd39d4f9790965e4b8f74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>MFC 應用程式精靈所建立的文件和檢視類別
「MFC 應用程式精靈」藉由建立基本架構文件和檢視類別，讓您在程式開發上能夠捷足先登。 您可以接著[將命令和訊息對應至這些類別](../mfc/reference/mapping-messages-to-functions.md)並且 Visual c + + 原始程式碼編輯器來撰寫其成員函式。  
  
 MFC 應用程式精靈所建立的文件類別衍生自類別[CDocument](../mfc/reference/cdocument-class.md)。 檢視類別衍生自[CView](../mfc/reference/cview-class.md)。 應用程式精靈給予這些類別的名稱以及包含這些的檔案，是以您在 [應用程式精靈] 對話方塊中提供的專案名稱為根據。 在 [應用程式精靈] 中，您可以使用 [產生的類別] 頁面修改預設名稱。  
  
 部分應用程式可能需要多個文件類別、檢視類別或框架視窗類別。 如需詳細資訊，請參閱[多重文件類型、 檢視和框架視窗](../mfc/multiple-document-types-views-and-frame-windows.md)。  
  
## <a name="see-also"></a>請參閱  
 [文件/檢視架構](../mfc/document-view-architecture.md)

