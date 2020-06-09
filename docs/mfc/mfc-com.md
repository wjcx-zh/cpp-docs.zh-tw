---
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: da194510938e3fe02eba5993182e811fdf2e1b7c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618018"
---
# <a name="mfc-com"></a>MFC COM

MFC 的子集是設計來支援 COM，而大部分的 Active Template Library （ATL）都是針對 COM 程式設計而設計的。 這一節的主題將描述 MFC 對 COM 的支援。

現用技術（例如 ActiveX 控制項、使用中的檔案內含專案、OLE 等等）使用元件物件模型（COM），讓軟體元件可以在網路環境中與彼此互動，而不論其建立的語言為何。 使用中技術可用來建立在桌上型電腦或網際網路上執行的應用程式。 如需詳細資訊，請參閱 COM 或[元件物件模型](/windows/win32/com/the-component-object-model)[簡介](../atl/introduction-to-com.md)。

主動式技術包含用戶端和伺服器技術，包括下列各項：

- ActiveX 控制項是可用於容器（例如網站）中的互動式物件。 如需 ActiveX 控制項的詳細資訊，請參閱：

  - [MFC ActiveX 控制項](mfc-activex-controls.md)

  - [網際網路上的 ActiveX 控制項](activex-controls-on-the-internet.md)

  - [總覽：網際網路](mfc-internet-programming-basics.md)

  - [升級要在網際網路上使用的現有 ActiveX 控制項](upgrading-an-existing-activex-control.md)

  - [對 ActiveX 控制項進行偵錯工具](/visualstudio/debugger/how-to-debug-an-activex-control)

- 動態指令碼控制來自瀏覽器或伺服器的一或多個 ActiveX 控制項的整合式行為。 如需有關動態指令碼的詳細資訊，請參閱[網際網路上的主動式技術](active-technology-on-the-internet.md)。

- [Automation](automation.md) （先前稱為 OLE Automation）讓一個應用程式可以操作在另一個應用程式中執行的物件，或「公開」物件以便操作。

   自動化物件可能是本機或遠端（在可透過網路存取的另一部電腦上）。 Aurotmation 可供 OLE 和 COM 物件使用。

- 本節也提供有關如何使用 MFC （例如[連接點](connection-points.md)）來撰寫 COM 元件的資訊。

如需仍然稱為 OLE 的討論，以及現在所謂的主動式技術，請參閱[ole](ole-in-mfc.md)上的主題。

## <a name="in-this-section"></a>本節內容

[主動式文件內含項目](active-document-containment.md)

[自動化](automation.md)

[連接點](connection-points.md)

[MFC ActiveX 控制項](mfc-activex-controls.md)

## <a name="see-also"></a>另請參閱

[概念](mfc-concepts.md)
