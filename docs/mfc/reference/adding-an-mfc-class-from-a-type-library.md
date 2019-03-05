---
title: 從類型程式庫加入 MFC 類別
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: e8264de2c717c874da157cb29ad5e336e3ecbd0f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301580"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>從類型程式庫加入 MFC 類別

使用此精靈，從可用的型別程式庫中的介面建立的 MFC 類別。 您可以將 MFC 類別新增至 [MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控制項](../../mfc/reference/creating-an-mfc-activex-control.md)。

> [!NOTE]
>  您不需要將類別加入從類型程式庫啟用自動化以建立您的 MFC 專案。

類型程式庫包含元件，其定義的方法，以及其參數和傳回型別所公開之介面的二進位的描述。 您必須針對會顯示在中註冊類型程式庫**可用的型別程式庫**Typelib 精靈加入類別中的清單。 請參閱 「 內部 Distributed COM:類型程式庫和語言整合 」 在 MSDN library，如需詳細資訊。

### <a name="to-add-an-mfc-class-from-a-type-library"></a>若要從型別程式庫新增 MFC 類別

1. 在**方案總管**或是[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)，以滑鼠右鍵按一下您要將類別加入專案的名稱。

1. 從捷徑功能表按一下 [新增]，然後按一下 [新增類別]。

1. 在[加入類別](../../ide/add-class-dialog-box.md)對話方塊，在 [範本] 窗格中，按一下**typelib 的 MFC 類別**，然後按一下 **開啟**以顯示[Typelib 精靈的 加入類別](../../mfc/reference/add-class-from-typelib-wizard.md).

在精靈中，您可以新增多個類型程式庫中的類別。 同樣地，您可以在單一精靈工作階段中，從一個以上的類型程式庫加入類別。

此精靈會建立衍生自 MFC 類別[COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)，為您從所選的型別程式庫中新增每個介面。 `COleDispatchDriver` 會實作 OLE automation 的用戶端。

## <a name="see-also"></a>另請參閱

[Automation 用戶端](../../mfc/automation-clients.md)<br/>
[Automation 用戶端：使用類型程式庫](../../mfc/automation-clients-using-type-libraries.md)
