---
title: MFC ActiveX 控制項：建立 Automation 伺服程式
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: f2c941e43e810845560b4c35c558ec70248c21ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622374"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC ActiveX 控制項：建立 Automation 伺服程式

您可以開發 MFC ActiveX 控制項做為 Automation 伺服器，以便以程式設計方式在另一個應用程式中內嵌該控制項，並從應用程式呼叫控制項中的方法。 這類控制項仍可裝載于 ActiveX 控制項容器中。

### <a name="to-create-a-control-as-an-automation-server"></a>若要建立控制項做為 Automation 伺服器

1. [建立](reference/mfc-activex-control-wizard.md)控制項。

1. [新增方法](mfc-activex-controls-methods.md)。

1. 覆寫[IsInvokeAllowed](reference/colecontrol-class.md#isinvokeallowed)。

1. 建立控制項。

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>以程式設計方式存取 Automation 伺服器中的方法

1. 建立應用程式，例如[MFC exe](reference/mfc-application-wizard.md)。

1. 在函式的開頭 `InitInstance` ，新增下列程式程式碼：

   [!code-cpp[NVC_MFC_AxCont#17](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. 在類別檢視中，以滑鼠右鍵按一下專案節點，然後選取 [**從 Typelib 加入類別**] 以匯入類型程式庫。

   這會將副檔名為 .h 和 .cpp 的檔案新增至專案。

1. 在您要在 ActiveX 控制項中呼叫一或多個方法的類別標頭檔中，新增下列程式程式碼： `#include filename.h` ，其中 file name 是您匯入類型程式庫時所建立的標頭檔名稱。

1. 在將對 ActiveX 控制項中的方法進行呼叫的函式中，加入程式碼來建立控制項包裝函式類別的物件，並建立 ActiveX 物件。 例如，下列 MFC 程式碼會具現化 `CCirc` 控制項、取得標題屬性，並在對話方塊中按一下 [確定] 按鈕時顯示結果：

   [!code-cpp[NVC_MFC_AxCont#18](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

如果您在應用程式中使用 ActiveX 控制項之後，將方法加入至其中，您可以藉由刪除匯入類型程式庫時所建立的檔案，開始在應用程式中使用最新版本的控制項。 然後再次匯入類型程式庫。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
