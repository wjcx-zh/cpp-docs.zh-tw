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
ms.openlocfilehash: e15a2a6bc016bf23bc0decf529b4c3ffeecc3a4c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621953"
---
# <a name="creating-document-frame-windows"></a>建立文件框架視窗

[[檔/視圖建立](document-view-creation.md)] 顯示[CDocTemplate](reference/cdoctemplate-class.md)物件如何協調建立框架視窗、檔和視圖，以及將它們全部連接在一起。 此函式的三個[CRuntimeClass](reference/cruntimeclass-structure.md)引數 `CDocTemplate` 會指定檔範本動態建立以回應使用者命令（例如 [檔案] 功能表上的 [新增] 命令或 MDI 視窗功能表上的 [新增視窗] 命令）的框架視窗、檔和視圖類別。 檔範本會儲存這份資訊，以供稍後在建立視圖和檔的框架視窗時使用。

若要讓[RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class)機制正常運作，您必須使用[DECLARE_DYNCREATE](reference/run-time-object-model-services.md#declare_dyncreate)宏來宣告您的衍生框架視窗類別。 這是因為架構必須使用類別的動態結構化機制來建立檔框架視窗 `CObject` 。

當使用者選擇建立檔的命令時，架構會在檔範本上呼叫以建立檔物件、其視圖，以及將顯示此視圖的框架視窗。 當它建立檔框架視窗時，檔範本會建立適當類別的物件，也就是衍生自[CFrameWnd](reference/cframewnd-class.md)的類別，適用于 SDI 應用程式或 MDI 應用程式的[CMDIChildWnd](reference/cmdichildwnd-class.md) 。 然後，架構會呼叫框架視窗物件的[LoadFrame](reference/cframewnd-class.md#loadframe)成員函式，以從資源取得建立資訊，並建立 Windows 視窗。 架構會將視窗控制碼附加至框架視窗物件。 然後，它會將此視圖建立為檔框架視窗的子視窗。

決定[何時要初始化](when-to-initialize-cwnd-objects.md) `CWnd` 衍生的物件時，請務必小心。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [從 CObject 衍生類別（其動態建立機制）](deriving-a-class-from-cobject.md)

- [檔/視圖建立（範本和框架視窗建立）](document-view-creation.md)

- [終結框架視窗](destroying-frame-windows.md)

## <a name="see-also"></a>另請參閱

[使用框架視窗](using-frame-windows.md)
