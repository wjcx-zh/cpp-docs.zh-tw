---
title: 建立主動式文件容器應用程式
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 965778fd5d17aa416b198c101edc3a445a39580b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257286"
---
# <a name="creating-an-active-document-container-application"></a>建立主動式文件容器應用程式

建立主動式文件容器應用程式的最簡單及最推薦的方式是使用 [MFC 應用程式精靈] 建立 MFC EXE 容器應用程式，然後將應用程式修改為支援主動式文件內含項目。

#### <a name="to-create-an-active-document-container-application"></a>建立主動式文件容器應用程式

1. 從**檔案**功能表上，按一下**專案**從**新增**子功能表。

1. 從左窗格中，按一下**Visual c + +** 專案類型。

1. 選取  **MFC 應用程式**從右窗格中。

1. 將專案命名為*MyProj*，按一下**確定**。

1. 選取 **複合文件支援**頁面。

1. 選取 **容器**或是**容器/全伺服器**選項。

1. 選取 **主動式文件容器**核取方塊。

1. 按一下 [ **完成**]。

1. 在 [MFC 應用程式精靈] 完成產生應用程式的程序時，使用 [方案總管] 開啟下列檔案：

   - *MyProjview.cpp*

1. 在  *MyProjview.cpp*，進行下列變更：

   - 以下列程式碼取代 `CMyProjView::OnPreparePrinting` 中的函式內容：

     [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting` 提供列印支援。 此程式碼會取代 `DoPreparePrinting`，這是預設的列印準備。

   主動式文件內含項目提供了改良的列印配置：

   - 您可以先呼叫主動式文件，透過其`IPrint`介面，並告知其自行列印。 這點不同於上一個 OLE 內含項目，容器不得不印表機將包含項目的影像呈現`CDC`物件。

   - 如果失敗則告知包含的項目自行透過列印其`IOleCommandTarget`介面

   - 如果失敗，則自行呈現項目。

   靜態成員函式 `COleDocObjectItem::OnPrint` 和 `COleDocObjectItem::OnPreparePrinting` (如上一個程式碼中所實作) 會處理這個改良的列印配置。

1. 加入您自己的所有實作並建置應用程式。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](../mfc/active-document-containment.md)
