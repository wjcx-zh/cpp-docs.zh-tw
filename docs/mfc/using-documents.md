---
title: "使用文件 |Microsoft 文件"
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
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 691d8d00b9c4671ea4b9c318313851a7fab73f7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-documents"></a>使用文件
文件和檢視一起運作：  
  
-   包含、 管理及顯示您的應用程式專屬[資料](../mfc/managing-data-with-document-data-variables.md)。  
  
-   提供介面組成[文件資料變數](../mfc/managing-data-with-document-data-variables.md)為了操作資料。  
  
-   參與[寫入和讀取檔案](../mfc/serializing-data-to-and-from-files.md)。  
  
-   參與[列印](../mfc/role-of-the-view-in-printing.md)。  
  
-   [處理](../mfc/handling-commands-in-the-document.md)大部分的應用程式的命令和訊息。  
  
 文件是特別專注於管理資料。 一般來說，儲存您的資料，在文件類別成員變數。 檢視會使用這些變數來存取資料，以供顯示及更新。 文件的預設序列化機制會管理讀取和寫入資料，從檔案。 文件也可以處理命令 (但不是 Windows 以外訊息**WM_COMMAND**)。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [從 CDocument 衍生文件類別](../mfc/deriving-a-document-class-from-cdocument.md)  
  
-   [使用文件資料變數管理資料](../mfc/managing-data-with-document-data-variables.md)  
  
-   [從檔案序列化資料](../mfc/serializing-data-to-and-from-files.md)  
  
-   [略過序列化機制](../mfc/bypassing-the-serialization-mechanism.md)  
  
-   [處理文件中的命令](../mfc/handling-commands-in-the-document.md)  
  
-   [OnNewDocument 成員函式](../mfc/reference/cdocument-class.md#onnewdocument)  
  
-   [DeleteContents 成員函式](../mfc/reference/cdocument-class.md#deletecontents)  
  
## <a name="see-also"></a>請參閱  
 [文件/檢視架構](../mfc/document-view-architecture.md)

