---
title: ActiveX 控制項容器：手動啟用 ActiveX 控制項內含項目
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 94ad6e8356b5dab54ae97dbdd90812039d1425c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322069"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX 控制項容器：手動啟用 ActiveX 控制項內含項目

當您使用 MFC 應用程式精靈產生應用程式時如果未啟用 ActiveX 控制項支援，您必須手動加入這項支援。 本文說明手動加入 ActiveX 控制項內含項目到現有的 OLE 容器應用程式的程序。 如果您事先知道在 OLE 容器中需要 ActiveX 控制支援,請參閱創建[MFC ActiveX 控制容器](../mfc/reference/creating-an-mfc-activex-control-container.md)的文章。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

> [!NOTE]
> 本文使用對話架構的 ActiveX 控制項容器專案 (名為 Container) 和內嵌控制項 (名為 Circ) 做為程序和程式碼的範例。

若要支援 ActiveX 控制項，您必須在兩個專案檔案中加入一行程式碼。

- 修改主對話方塊的`InitInstance`功能 (見於"容器"中)。CPP) 由 MFC 應用程式精靈呼叫[AfxEnableControl 容器](reference/ole-initialization.md#afxenablecontrolcontainer),如以下範例所示:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- 將下列項目加入至您的 STDAFX.H 標頭檔：

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

完成這些步驟後,單擊「**生成**」功能表上的 **「生成」來**重建專案。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](../mfc/activex-control-containers.md)
