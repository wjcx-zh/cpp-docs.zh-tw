---
title: ActiveX 控制項容器：手動啟用 ActiveX 控制項內含項目
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: a8092a77020695163ce4fbacf7eeea2650ae9f86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625107"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX 控制項容器：手動啟用 ActiveX 控制項內含項目

當您使用 MFC 應用程式精靈產生應用程式時如果未啟用 ActiveX 控制項支援，您必須手動加入這項支援。 本文說明手動加入 ActiveX 控制項內含項目到現有的 OLE 容器應用程式的程序。 如果您事先知道您的 OLE 容器中需要 ActiveX 控制項支援，請參閱[建立 MFC ActiveX 控制項容器一](reference/creating-an-mfc-activex-control-container.md)文。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

> [!NOTE]
> 本文使用對話架構的 ActiveX 控制項容器專案 (名為 Container) 和內嵌控制項 (名為 Circ) 做為程序和程式碼的範例。

若要支援 ActiveX 控制項，您必須在兩個專案檔案中加入一行程式碼。

- 修改主要對話的函式 `InitInstance` （可在 CONTAINER 中找到）。CPP），由 MFC 應用程式精靈呼叫[AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer)，如下列範例所示：

   [!code-cpp[NVC_MFCOleContainer#34](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- 將下列項目加入至您的 STDAFX.H 標頭檔：

   [!code-cpp[NVC_MFCOleContainer#36](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

完成這些步驟之後，按一下 [**建立**] 功能表上的 [**建立**] 來重建您的專案。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](activex-control-containers.md)
