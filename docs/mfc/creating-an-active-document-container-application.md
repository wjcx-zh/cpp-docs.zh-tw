---
title: 建立主動式文件容器應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 880c6953addd0ec7db3abf5864010bd472d2d5a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341345"
---
# <a name="creating-an-active-document-container-application"></a>建立主動式文件容器應用程式
建立主動式文件容器應用程式的最簡單及最推薦的方式是使用 [MFC 應用程式精靈] 建立 MFC EXE 容器應用程式，然後將應用程式修改為支援主動式文件內含項目。  
  
#### <a name="to-create-an-active-document-container-application"></a>建立主動式文件容器應用程式  
  
1.  從**檔案**功能表上，按一下 **專案**從**新增**子功能表。  
  
2.  從左窗格中，按一下  **Visual c + +** 專案類型。  
  
3.  選取**MFC 應用程式**從右窗格。  
  
4.  將專案命名`MyProj`，按一下 **確定**。  
  
5.  選取**複合文件支援**頁面。  
  
6.  選取**容器**或**容器/全伺服器**選項。  
  
7.  選取**主動式文件容器**核取方塊。  
  
8.  按一下 [ **完成**]。  
  
9. 在 [MFC 應用程式精靈] 完成產生應用程式的程序時，使用 [方案總管] 開啟下列檔案：  
  
    -   MyProjview.cpp  
  
10. 在 MyProjview.cpp 中進行下列變更：  
  
    -   以下列程式碼取代 `CMyProjView::OnPreparePrinting` 中的函式內容：  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting` 提供列印支援。 此程式碼會取代 `DoPreparePrinting`，這是預設的列印準備。  
  
     主動式文件內含項目提供了改良的列印配置：  
  
    -   您可以先呼叫使用中文件，透過其`IPrint`介面，並告訴它本身。 這點不同於先前 OLE 內含項目，容器來呈現包含的項目拖曳至印表機的映像必須`CDC`物件。  
  
    -   如果失敗，告訴 包含的項目時列印本身透過其`IOleCommandTarget`介面  
  
    -   如果失敗，則自行呈現項目。  
  
     靜態成員函式 `COleDocObjectItem::OnPrint` 和 `COleDocObjectItem::OnPreparePrinting` (如上一個程式碼中所實作) 會處理這個改良的列印配置。  
  
11. 加入您自己的所有實作並建置應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [主動式文件內含項目](../mfc/active-document-containment.md)

