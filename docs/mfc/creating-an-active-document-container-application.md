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
ms.openlocfilehash: 860a8531a96a0671c808dba13523b492026eafe0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616345"
---
# <a name="creating-an-active-document-container-application"></a>建立主動式文件容器應用程式

建立主動式文件容器應用程式的最簡單及最推薦的方式是使用 [MFC 應用程式精靈] 建立 MFC EXE 容器應用程式，然後將應用程式修改為支援主動式文件內含項目。

#### <a name="to-create-an-active-document-container-application"></a>建立主動式文件容器應用程式

1. 從 [檔案 **] 功能表中**，按一下 [**新增**] 子功能表中的 [**專案**]。

1. 在左窗格中，按一下 [ **Visual C++** 專案類型]。

1. 從右窗格中選取 [ **MFC 應用程式**]。

1. 將專案命名為*myproj.csproj*，然後按一下 **[確定]**。

1. 選取 [**複合檔案支援**] 頁面。

1. 選取 [**容器**] 或 [**容器/完整伺服器**] 選項。

1. 選取 [**活動文檔容器**] 核取方塊。

1. 按一下 [完成] 。

1. 在 [MFC 應用程式精靈] 完成產生應用程式的程序時，使用 [方案總管] 開啟下列檔案：

   - *MyProjview.cpp*

1. 在*MyProjview*中，進行下列變更：

   - 以下列程式碼取代 `CMyProjView::OnPreparePrinting` 中的函式內容：

     [!code-cpp[NVC_MFCDocView#56](codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting` 提供列印支援。 此程式碼會取代 `DoPreparePrinting`，這是預設的列印準備。

   主動式文件內含項目提供了改良的列印配置：

   - 您可以先透過其介面呼叫使用中的檔 `IPrint` ，並告訴它自己列印。 這與先前的 OLE 內含專案不同，因為容器必須在印表機物件上呈現所包含專案的影像 `CDC` 。

   - 如果失敗，請告知包含的專案透過其介面自行列印 `IOleCommandTarget`

   - 如果失敗，則自行呈現項目。

   靜態成員函式 `COleDocObjectItem::OnPrint` 和 `COleDocObjectItem::OnPreparePrinting` (如上一個程式碼中所實作) 會處理這個改良的列印配置。

1. 加入您自己的所有實作並建置應用程式。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](active-document-containment.md)
