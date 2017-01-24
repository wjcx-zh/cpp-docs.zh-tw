---
title: "文件樣板建立 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "建構函式 [C++], 文件範本"
  - "文件樣板"
  - "文件樣板, 建立"
  - "MFC, 文件樣板"
  - "範本, 文件樣板"
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文件樣板建立
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當建立新的文件以回應 `New` 或從檔案功能表的 **Open** 命令，文件範本也會建立檢視文件的新的框架視窗。  
  
 文件樣板建構函式指定何種類型的資料、視窗和檢視範本可以建立。  您可以對文件樣板建構函式的引數所決定。  下列程式碼說明 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) 的建立應用程式的:  
  
 [!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/CPP/document-template-creation_1.cpp)]  
  
 將新的 `CMultiDocTemplate` 物件的指標當做 [AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md)的引數。  傳遞給 `CMultiDocTemplate` 建構函式的引數是由資源 ID 與文件類型的功能表和快速鍵和對 [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md) 巨集的三個用途。  `RUNTIME_CLASS` 傳回 C\+\+ 類別的 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 物件做為其引數。  三個 `CRuntimeClass` 物件傳遞至資訊需要在文件建立程序期間建立指定的類別新物件的資料範本建構函式提供。  這個範例會示範建立連接的 `CScribView` 物件的 `CScribDoc` 物件資料範本的建立。  檢視會以標準 MDI 子框架視窗框架。  
  
## 請參閱  
 [文件範本和文件\/檢視建立流程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文件\/檢視建立](../mfc/document-view-creation.md)   
 [MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)   
 [建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)