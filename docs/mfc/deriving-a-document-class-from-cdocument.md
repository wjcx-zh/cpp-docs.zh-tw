---
title: "從 CDocument 衍生文件類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e5c128a2a2e32b5e4854725354ed484a335ab0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="deriving-a-document-class-from-cdocument"></a>從 CDocument 衍生文件類別
文件包含並管理您的應用程式資料。 若要使用 MFC 應用程式精靈提供的文件類別，您必須執行下列作業：  
  
-   自**CDocument**每種類型的文件。  
  
-   加入成員變數來儲存每個文件的資料。  
  
-   覆寫**CDocument**的`Serialize`文件類別中的成員函式。 `Serialize`寫入並讀取文件的資料磁碟。  
  
## <a name="other-document-functions-often-overridden"></a>通常被覆寫的其他文件函式  
 您也可以覆寫其他**CDocument**成員函式。 特別是，您通常需要覆寫[OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)和[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)來初始化文件的資料成員和[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)終結動態配置的資料。 如需覆寫成員的資訊，請參閱類別[CDocument](../mfc/reference/cdocument-class.md)中*MFC 參考*。  
  
## <a name="see-also"></a>請參閱  
 [使用文件](../mfc/using-documents.md)

