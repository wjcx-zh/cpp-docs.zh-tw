---
title: "如何：將現有的 MFC 功能區轉換為功能區資源 | Microsoft Docs"
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
  - "MFC 功能區, 轉換為功能區資源"
  - "功能區資源, 從 MFC 功能區轉換"
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將現有的 MFC 功能區轉換為功能區資源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

功能區資源比更容易視覺化，修改和維護手動撰寫功能區。  本主題說明如何轉換手動撰寫在 MFC 專案的功能區到功能區資源。  
  
 您必須擁有程式碼使用 MFC 功能區類別，例如， [CMFCRibbonBar 類別](../mfc/reference/cmfcribbonbar-class.md)的現有的 MFC 專案。  
  
### 將 MFC 功能區轉換成功能區資源  
  
1.  在 Visual Studio 中，在現有的 MFC 專案，請開啟 CMFCRibbonBar 物件初始化的原始程式檔。  通常，檔案是 mainfrm.cpp。  在功能區上的初始化程式碼後面加入下列程式碼。  
  
    ```  
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");  
    ```  
  
     儲存並關閉檔案。  
  
2.  建置並執行 MFC 應用程式，然後在記事本中，開啟 RibbonOutput.txt 並複製其內容。  
  
3.  在 Visual Studio 中，按一下 \[**專案**\] 功能表上，按一下 \[**加入資源**\]。  在 \[**加入資源** \] 對話方塊中，選取 \[**功能區** \]，然後按一下 \[**新增**\]。  
  
     Visual Studio 會建立功能區資源並在設計檢視中將它開啟。  功能區資源 ID 是 IDR\_RIBBON1，顯示在 \[**資源檢視**\] 中。  功能區 XML ribbon1.mfcribbon\) 檔案中定義。  
  
4.  在 Visual Studio 中，開啟 ribbon1.mfcribbon 毫秒，刪除其內容，然後貼上 RibbonOutput.txt 內容，您複製之前。  儲存並關閉 ribbon1.mfcribbon 毫秒。  
  
5.  再次開啟 CMFCRibbonBar 物件初始化的原始程式檔 \(通常， mainfrm.cpp\) 和註解現有功能區程式碼。  在註解的程式碼後面加入下列程式碼。  
  
    ```  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);  
    ```  
  
6.  建置專案並執行程式。  
  
## 請參閱  
 [功能區設計工具 \(MFC\)](../mfc/ribbon-designer-mfc.md)