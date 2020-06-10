---
title: ActiveX 控制項容器
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: 42fa18c41ebd960aa8de080df00556ad5c909d40
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620760"
---
# <a name="activex-control-containers"></a>ActiveX 控制項容器

ActiveX 控制項容器是一種完全支援 ActiveX 控制項的容器，可以將其合併至自己的視窗或對話方塊中。 ActiveX 控制項可讓您在許多開發專案中重複使用的軟體項目。 控制項可讓您應用程式的使用者存取資料庫、監視資料，以及在您的應用程式中做出各種選擇。 如需 ActiveX 控制項的詳細資訊，請參閱[MFC Activex 控制項](mfc-activex-controls.md)一文。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

控制項容器在專案中通常會有兩種形式：

- 對話方塊和類似對話方塊的視窗 (例如表單檢視)，其中 ActiveX 控制項會用於對話方塊中的某個位置。

- 應用程式中的視窗，其中 ActiveX 控制項用於工具列，或使用者視窗中的其他位置。

ActiveX 控制項容器會透過公開的[方法](mfc-activex-controls-methods.md)和[屬性](mfc-activex-controls-properties.md)，與控制項互動。 這些方法和屬性可以透過控制項容器存取和修改，您可以透過 ActiveX 控制項容器專案中的包裝函式類別進行存取。 內嵌的 ActiveX 控制項也可以藉由引發（傳送）[事件](mfc-activex-controls-events.md)來通知容器已發生動作，以與容器互動。 控制項容器可以選擇是否要針對這些通知採取行動。

其他文章中討論的幾個主題，從建立 ActiveX 控制項容器專案到與使用 Visual C++ 建置之 ActiveX 控制項容器相關的基礎實作問題：

- [建立 MFC ActiveX 控制項容器](reference/creating-an-mfc-activex-control-container.md)

- [ActiveX 控制項的容器](containers-for-activex-controls.md)

- [ActiveX 控制項容器：手動啟用 ActiveX 控制項內含項目](activex-control-containers-manually-enabling-activex-control-containment.md)

- [ActiveX 控制項容器：將控制項插入控制項容器應用程式中](inserting-a-control-into-a-control-container-application.md)

- [ActiveX 控制項容器：將 ActiveX 控制項連接至成員變數](activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [ActiveX 控制項容器：處理來自 ActiveX 控制項的事件](activex-control-containers-handling-events-from-an-activex-control.md)

- [ActiveX 控制項容器：檢視和修改控制項屬性](activex-control-containers-viewing-and-modifying-control-properties.md)

- [ActiveX 控制項容器：在 ActiveX 控制項容器中程式設計 ActiveX 控制項](programming-activex-controls-in-a-activex-control-container.md)

- [ActiveX 控制項容器：在非對話方塊容器中使用控制項](activex-control-containers-using-controls-in-a-non-dialog-container.md)

如需在對話方塊中使用 ActiveX 控制項的詳細資訊，請參閱[對話方塊編輯器](../windows/dialog-editor.md)主題。

如需使用 Visual C++ 和 MFC ActiveX 控制項類別來說明開發 ActiveX 控制項詳細資料的文章清單，請參閱[Mfc activex 控制項](mfc-activex-controls.md)。 這些文章會依功能分類為不同群組。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
