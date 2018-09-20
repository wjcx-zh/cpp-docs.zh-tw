---
title: 建立 MFC ActiveX 控制項容器 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.activex.container
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37119934a70f8a68d32ed83699fa6deb012d8879
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404432"
---
# <a name="creating-an-mfc-activex-control-container"></a>建立 MFC ActiveX 控制項容器

ActiveX 控制項容器是父代程式，提供 ActiveX (先前稱為 OLE) 控制項執行的環境。 您可以建立應用程式包含 ActiveX 控制項或不以 MFC，但更容易使用 MFC 進行。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](../activex-controls.md)。

建立 MFC 容器計劃使用[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)可讓您存取的 ActiveX 控制項和自動化的 MFC 和 ActiveX 類別所實作的許多功能。 這些功能包括視覺化編輯，自動化、 建立複合的檔案，以及支援的控制項。 父代程式將支援的 MFC 應用程式精靈視覺化編輯選項，包括建立容器、 迷你伺服器、 全伺服器和程式，為容器和伺服器。

- **新的 MFC 應用程式**。 若要建立新的 MFC 計畫，其中包含自動化，視覺化編輯，複合檔案，或控制支援、 使用 MFC 應用程式精靈 並選擇適當的自動化選項。

- **現有的 MFC 應用程式**。 如果您要新增控制項內含項目至現有的 MFC 應用程式，請參閱[OLE 控制項容器： 手動啟用 OLE 控制項內含項目](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)。

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>若要建立 ActiveX 容器任何下列類型的應用程式

1. [容器](../../mfc/containers.md)

1. [視覺化編輯](../../mfc/ole-mfc.md)

1. [MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>另請參閱

[Visual C++ 專案類型](../../ide/visual-cpp-project-types.md)

