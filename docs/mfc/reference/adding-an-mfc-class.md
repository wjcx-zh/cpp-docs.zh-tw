---
title: 新增 MFC 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.adding.mfc
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86e42ab5c2e8e15f5f56687b5ca99d160270017b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436360"
---
# <a name="adding-an-mfc-class"></a>加入 MFC 類別

若要新增至您的專案從 Microsoft Foundation Class (MFC) 程式庫類別衍生的類別，請使用**加入類別**命令可從[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)。 指定新的類別名稱、 選取基底類別，然後選取 [與它相關聯 （如果有的話）] 對話方塊中的識別碼。 程式碼精靈建立標頭檔與實作檔，並將它們新增至您的專案。

> [!NOTE]
>  您可以將 MFC 類別加入 ATL COM 應用程式，如果您最初[建立應用程式與 MFC 支援](../../atl/reference/mfc-support-in-atl-projects.md)。 您也可以將 MFC 類別加入 MFC 支援的 Win32 專案中。

### <a name="to-add-an-mfc-class-to-your-project"></a>若要加入專案中的 MFC 類別

1. 從 類別檢視，以滑鼠右鍵按一下專案名稱。 按一下 [**新增**，然後按一下**加入類別**以開啟[加入類別](../../ide/add-class-dialog-box.md)] 對話方塊。

1. 在 範本 窗格中，選取**MFC 類別**然後按**新增** 按鈕。

1. 定義新的類別中的設定[MFC 類別精靈](../../mfc/reference/mfc-add-class-wizard.md) 對話方塊。

1. 按一下 **完成**來關閉精靈，然後在 類別檢視中檢視新的類別。 您也可以檢視中的精靈所建立的檔案**方案總管 中**。

## <a name="see-also"></a>另請參閱

[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[加入類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[類別概觀](../../mfc/class-library-overview.md)

