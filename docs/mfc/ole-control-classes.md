---
title: OLE 控制項類別
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: 5aa3899dca5a42cf789dc6dfd4701547495ec618
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617771"
---
# <a name="ole-control-classes"></a>OLE 控制項類別

這些是您在撰寫 OLE 控制項時使用的主要類別。 `COleControlModule`OLE 控制項模組中的類別就像應用程式中的[CWinApp](reference/cwinapp-class.md)類別。 每個模組會實作一個或多個 OLE 控制項；這些控制項是由 `COleControl` 物件表示。 這些控制項會使用 `CConnectionPoint` 物件與其容器通訊。

`CPictureHolder` 和 `CFontHolder` 類別會封裝圖片和字型的 COM 介面，而 `COlePropertyPage` 和 `CPropExchange` 類別可協助您為您的控制項實作屬性頁和屬性持續性。

[COleControlModule](reference/colecontrolmodule-class.md)<br/>
取代您的 OLE 控制項模組的 `CWinApp` 類別。 衍生自 `COleControlModule` 類別以開發 OLE 控制項模組物件。 提供成員函式以供初始化您的 OLE 控制項模組。

[COleControl](reference/colecontrol-class.md)<br/>
衍生自 `COleControl` 類別以開發 OLE 控制項。 衍生自 `CWnd`，此類別會繼承 Windows 視窗物件的所有功能以及其他 OLE 特定功能，例如事件引發以及支援方法和屬性。

[CConnectionPoint](reference/cconnectionpoint-class.md)<br/>
`CConnectionPoint` 類別定義了一種用來與其他 OLE 物件通訊的特殊介面類型，稱為「連接點」。 連接點會實作可以對其他物件起始動作 (例如引發事件和變更通知) 的輸出介面。

[CPictureHolder](reference/cpictureholder-class.md)<br/>
封裝 Windows 圖片物件和 `IPicture` COM 介面的功能；用來實作 OLE 控制項的自訂圖片屬性。

[CFontHolder](reference/cfontholder-class.md)<br/>
封裝 Windows 字型物件和 `IFont` COM 介面的功能；用來實作 OLE 控制項的內建字型屬性。

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
在類似對話方塊的圖形介面中顯示 OLE 控制項的屬性。

[CPropExchange](reference/cpropexchange-class.md)<br/>
支援 OLE 控制項的屬性持續性實作。 類似于對話方塊的[CDataExchange](reference/cdataexchange-class.md) 。

[CMonikerFile](reference/cmonikerfile-class.md)<br/>
取得 Moniker 或者可以製作成 Moniker 的字串表示，並且與以 Moniker 為名的串流進行同步繫結。

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)<br/>
運作方式類似 `CMonikerFile`；不過，這是與以 Moniker 為名的串流進行非同步繫結。

[CDataPathProperty](reference/cdatapathproperty-class.md)<br/>
實作可以非同步載入的 OLE 控制項屬性。

[CCachedDataPathProperty](reference/ccacheddatapathproperty-class.md)<br/>
實作非同步傳輸且在記憶體檔案中快取的 OLE 控制項屬性。

[COleCmdUI](reference/colecmdui-class.md)<br/>
允許現用文件接收來自其容器的使用者介面的命令 (例如 FileNew、Open、Print 等)，並允許容器接收來自現用文件使用者介面的命令。

[COleSafeArray](reference/colesafearray-class.md)<br/>
用來處理任意類型和維度的陣列。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
