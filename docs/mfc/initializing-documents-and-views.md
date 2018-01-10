---
title: "初始化文件和檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f80d870f9804454dc652fdda00f34fcdb7a52062
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-documents-and-views"></a>初始化文件和檢視
文件是以兩種不同的方式建立，因此您的文件類別必須支援這兩種方式。 首先，使用者可以使用 [開新檔案] 命令建立新的空白文件。 在此情況下，初始化文件的覆寫中[OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)類別成員函式[CDocument](../mfc/reference/cdocument-class.md)。 其次，使用者可以使用 [檔案] 功能表的 [開啟] 命令建立從某個檔案讀取內容的新文件。 在此情況下，初始化文件的覆寫中[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)類別成員函式**CDocument**。 如果兩種初始化方式相同，您可以從兩個覆寫中呼叫一個共同的成員函式，或者 `OnOpenDocument` 可以呼叫 `OnNewDocument` 以初始化全新的文件後再完成開啟作業。  
  
 在建立其文件後會建立檢視。 初始化檢視的最佳時機是在架構完成建立文件、框架視窗與檢視之後。 您可以藉由覆寫中初始化檢視[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)成員函式[CView](../mfc/reference/cview-class.md)。 如果您需要重新初始化或調整任何項目每次文件變更，您可以覆寫[OnUpdate](../mfc/reference/cview-class.md#onupdate)。  
  
## <a name="see-also"></a>請參閱  
 [初始化及清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)

