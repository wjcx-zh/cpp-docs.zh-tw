---
title: 將 ATL 支援加入至 MFC 專案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.adding.atl.mfc
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc0d21202478a02980dbc94dc866b769c3c71a9b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429730"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>將 ATL 支援加入至 MFC 專案

如果您已經建立 MFC 架構的應用程式，然後您可以新增支援的 Active Template Library (ATL) 中輕鬆執行 MFC 專案精靈] 的 [新增 ATL 支援。

> [!NOTE]
>  ATL 和 MFC 不正式支援 Visual Studio 的 Express 版本中。

> [!NOTE]
>  這項支援只適用於新增至 MFC 可執行檔或 DLL 專案的簡單 COM 物件。 您可以將其他的 COM 物件 （包括 ActiveX 控制項） 新增至 MFC 專案中，但物件可能無法如預期般運作。

### <a name="to-add-atl-support-to-your-mfc-project"></a>若要將 ATL 支援加入至 MFC 專案

1. 在 [方案總管] 中，以滑鼠右鍵按一下您要將 ATL 支援加入的專案。

1. 在捷徑功能表，按一下 **新增**，然後按一下**加入類別**。

1. 選取 **新增 ATL 支援加入至 MFC 專案**圖示。

    > [!NOTE]
    >  這個圖示位在 [ATL] 資料夾**分類**窗格。

1. 出現提示時，按一下**是**新增 ATL 支援。

如需有關如何將 ATL 支援加入變更您的 MFC 專案的程式碼的詳細資訊，請參閱[詳細資料的 ATL 支援加入 ATL 精靈](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>另請參閱

[加入類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
