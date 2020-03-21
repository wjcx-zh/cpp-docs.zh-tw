---
title: 建立 MFC ActiveX 控制項容器
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.container
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
ms.openlocfilehash: 27f229a23595d4842a77409a3cedc7a57aa43e6c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079430"
---
# <a name="creating-an-mfc-activex-control-container"></a>建立 MFC ActiveX 控制項容器

ActiveX 控制項容器是一個父程式，可提供要執行之 ActiveX （先前稱為 OLE）控制項的環境。 您可以建立能夠包含 ActiveX 控制項的應用程式（不論是否使用 MFC），但使用 MFC 更容易。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](../activex-controls.md)。

使用[Mfc 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)來建立 mfc 容器程式，可讓您存取 Mfc 和 activex 類別所實作為之 ActiveX 控制項和自動化的許多功能。 這些功能包括視覺編輯、自動化、建立複合檔案和控制項的支援。 您的父程式將支援的 MFC 應用程式 [視覺編輯] 選項包括建立容器、迷你伺服器、完整伺服器，以及同時為容器和伺服器的程式。

- **新的 MFC 應用程式**。 若要建立包含自動化、視覺編輯、複合檔案或控制項支援的新 MFC 程式，請使用 [MFC 應用程式精靈]，然後選擇適當的自動化選項。

- **現有的 MFC 應用程式**。 如果您要將控制項內含專案加入現有的 MFC 應用程式，請參閱[Ole 控制項容器：手動啟用 Ole 控制項](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)內含專案。

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>為下列任何類型的應用程式建立 ActiveX 容器

1. [容器](../../mfc/containers.md)

1. [視覺編輯](../../mfc/ole-mfc.md)

1. [MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++ 專案類型](../../build/reference/visual-cpp-project-types.md)
