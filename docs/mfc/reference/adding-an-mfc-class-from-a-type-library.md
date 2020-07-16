---
title: 從類型程式庫加入 MFC 類別
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: 4e8d0f74a73048f172a8030d4bfb081c803e7170
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405113"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>從類型程式庫加入 MFC 類別

使用此 wizard 從可用類型程式庫中的介面建立 MFC 類別。 您可以將 MFC 類別新增至 [MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控制項](../../mfc/reference/creating-an-mfc-activex-control.md)。

> [!NOTE]
> 您不需要建立已啟用自動化的 MFC 專案，即可從類型程式庫加入類別。

類型程式庫包含元件所公開介面的二進位描述，並定義方法及其參數和傳回類型。 您的型別程式庫必須註冊，才會出現在 [從 Typelib 新增類別] 中的 [**可用的型別程式庫**] 清單中。

### <a name="to-add-an-mfc-class-from-a-type-library"></a>從類型程式庫加入 MFC 類別

1. 在**方案總管**或[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下您要新增類別的專案名稱。

1. 從捷徑功能表按一下 [新增]****，然後按一下 [新增類別]****。

1. 在 [[加入類別](../../ide/add-class-dialog-box.md)] 對話方塊的 [範本] 窗格中，按一下 [typelib 中的**MFC 類別**]，然後按一下 [**開啟**] 以顯示 [[從 typelib 加入類別] Wizard](../../mfc/reference/add-class-from-typelib-wizard.md)。

在嚮導中，您可以在類型程式庫中加入一個以上的類別。 同樣地，您也可以在單一 wizard 會話中，從一個以上的類型程式庫加入類別。

此 wizard 會針對您從選取的類型程式庫加入的每個介面，建立一個衍生自[COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)的 MFC 類別。 `COleDispatchDriver`執行 OLE automation 的用戶端。

## <a name="see-also"></a>另請參閱

[Automation 用戶端](../../mfc/automation-clients.md)<br/>
[Automation 用戶端：使用型別程式庫](../../mfc/automation-clients-using-type-libraries.md)
