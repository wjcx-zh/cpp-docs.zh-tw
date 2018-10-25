---
title: ActiveX 控制項容器： 手動啟用 ActiveX 控制項內含項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f684bbb287213ad0cbe6d490c1bef869f5ffc9db
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077773"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX 控制項容器：手動啟用 ActiveX 控制項內含項目

當您使用 MFC 應用程式精靈產生應用程式時如果未啟用 ActiveX 控制項支援，您必須手動加入這項支援。 本文說明手動加入 ActiveX 控制項內含項目到現有的 OLE 容器應用程式的程序。 如果您事先知道您 OLE 容器需要 ActiveX 控制項支援，請參閱文章[建立 MFC ActiveX 控制項容器](../mfc/reference/creating-an-mfc-activex-control-container.md)。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

> [!NOTE]
>  本文使用對話架構的 ActiveX 控制項容器專案 (名為 Container) 和內嵌控制項 (名為 Circ) 做為程序和程式碼的範例。

若要支援 ActiveX 控制項，您必須在兩個專案檔案中加入一行程式碼。

- 修改主對話方塊的`InitInstance`函式 （在容器中找到。CPP) 呼叫的 MFC 應用程式精靈[AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer)，如下列範例所示：

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- 將下列項目加入至您的 STDAFX.H 標頭檔：

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

您已完成這些步驟之後，重建您的專案，依序按一下**建置**上**建置**功能表。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](../mfc/activex-control-containers.md)

