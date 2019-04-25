---
title: 建立文件框架視窗
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
ms.openlocfilehash: 66a951994a75cbd99debeb2c6511739411cdd470
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174025"
---
# <a name="creating-document-frame-windows"></a>建立文件框架視窗

[文件/檢視建立](../mfc/document-view-creation.md)示範如何[CDocTemplate](../mfc/reference/cdoctemplate-class.md)物件用來協調建立框架視窗、 文件及檢視並將它們所有的連接。 三個[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)引數`CDocTemplate`建構函式指定的框架視窗、 文件和文件範本以動態方式建立以回應使用者命令，例如新的命令，在檔案上的檢視類別功能表或在 MDI 視窗 功能表上的新視窗 命令。 建立檢視和文件框架視窗時，文件範本會儲存此資訊供日後使用。

針對[RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)機制可以正常運作，您的衍生框架視窗類別必須以宣告[DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)巨集。 這是因為架構需要建立文件框架視窗類別的動態建構機制`CObject`。

當使用者選擇建立文件的命令時，架構會呼叫文件範本來建立文件物件、 它的檢視和框架視窗會顯示在檢視時。 當它建立文件框架視窗時，此文件範本會建立適當的類別的物件 — 類別衍生自[CFrameWnd](../mfc/reference/cframewnd-class.md) SDI 應用程式，或從[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) mdi應用程式。 架構接著會呼叫框架視窗物件的[LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)若要建立資訊與資源，並建立 Windows 視窗的成員函式。 此架構會將視窗控制代碼附加至框架視窗物件。 然後它會做為文件框架視窗的子視窗建立檢視。

請小心決定[初始化的時機](../mfc/when-to-initialize-cwnd-objects.md)您`CWnd`-衍生物件。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [衍生自 CObject （動態建立的機制） 的類別](../mfc/deriving-a-class-from-cobject.md)

- [（範本和框架視窗建立） 的文件/檢視建立](../mfc/document-view-creation.md)

- [終結框架視窗](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>另請參閱

[使用框架視窗](../mfc/using-frame-windows.md)
