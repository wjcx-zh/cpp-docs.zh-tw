---
title: MFC ActiveX 控制項： 建立 Automation 伺服程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e37e6183ca840067ceca47dd48f3b24d7b3b98c7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074536"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC ActiveX 控制項：建立 Automation 伺服程式

您可以為 Automation 伺服程式為了以程式設計方式內嵌在另一個應用程式中的該控制項，並在控制項中呼叫方法，從應用程式開發 MFC ActiveX 控制項。 這類控制項仍然可供裝載 ActiveX 控制項容器中。

### <a name="to-create-a-control-as-an-automation-server"></a>要建立的控制項為 Automation 伺服器

1. [建立](../mfc/reference/mfc-activex-control-wizard.md)控制項。

1. [將方法加入](../mfc/mfc-activex-controls-methods.md)。

1. 覆寫[IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed)。

1. 建置控制項。

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>以程式設計方式存取 Automation 伺服器中的方法

1. 建立應用程式，例如，an [MFC exe](../mfc/reference/mfc-application-wizard.md)。

1. 在開頭`InitInstance`函式中，加入下列一行：

   [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. 在 類別檢視，以滑鼠右鍵按一下專案節點，然後選取**從 typelib 加入類別**匯入類型程式庫。

   這會將具有檔案名稱副檔名.h 和.cpp 檔案加入專案。

1. 標頭檔的類別，您會呼叫一或多個方法的 ActiveX 控制項中，加入下面這一行： `#include filename.h`，其中的檔案名稱是當您匯入類型程式庫時所建立的標頭檔的名稱。

1. 在函數呼叫進行 ActiveX 控制項中的方法中，加入程式碼會建立控制項的包裝函式類別的物件，並建立 ActiveX 物件。 例如，下列的 MFC 程式碼會具現化`CCirc`控制項，取得 [標題] 屬性中，並在對話方塊中按一下 [確定] 按鈕時顯示的結果：

   [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

如果您的應用程式中使用它之後，您可以將加入 ActiveX 控制項的方法，您可以開始在應用程式中使用控制項的最新版本，藉由刪除匯入類型程式庫時所建立的檔案。 然後再次匯入類型程式庫。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

