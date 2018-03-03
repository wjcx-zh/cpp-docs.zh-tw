---
title: "主動式文件內含項目範例： Office 文件夾 |Microsoft 文件"
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
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00451b41b047f433929ad58e4b275eb413f4e22e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="example-of-active-document-containment-office-binder"></a>主動式文件內含項目範例：Office 文件夾
Microsoft Office Binder 是現用文件容器的範例。 Office Binder 如一般容器一樣包含兩個主要窗格。 左窗格包含對應至 Binder 中的現用文件的圖示。 每份文件稱為*區段*內繫結器。 例如，Binder 可以包含 Word 文件、PowerPoint 檔和 Excel 試算表等等。  
  
 按一下左窗格中的圖示可啟動對應的現用文件。 Binder 的右窗格接著會顯示目前所選取現用文件的內容。  
  
 如果您開啟並啟動在 Binder 中的 Word 文件，Word 功能表列和工具列會顯示在檢視的頂端，您可以使用所有 Word 命令或工具來編輯文件的內容。 不過，功能表列是 Binder 的功能表列和 Word 的功能表列的組合。 由於 Binder 和 Word 都有**協助**功能表、 個別功能表的內容會合併。 諸如 Office Binder 的現用文件容器會自動提供**協助**功能表合併; 如需詳細資訊，請參閱[說明功能表合併](../mfc/help-menu-merging.md)。  
  
 當您選取另一個應用程式類型的現用文件時，Binder 的介面會變更為可容納該現用文件的應用程式類型。 例如，如果 Binder 包含 Excel 試算表，則當您選取 Excel 試算表區段時，您會注意到 Binder 中的功能表會變動。  
  
 當然，其他類型的容器會在 Binder 旁邊。 [檔案總管] 使用一般的雙窗格介面，其左窗格使用樹狀目錄控制項來顯示磁碟機或網路中的目錄的階層式清單，而右窗格則顯示目前所選取目錄中包含的檔案。 網際網路瀏覽器類型的容器 （例如 Microsoft Internet Explorer)，而不是使用雙窗格介面，通常具有單一框架，並提供使用超連結的導覽。  
  
## <a name="see-also"></a>請參閱  
 [主動式文件內含項目](../mfc/active-document-containment.md)

