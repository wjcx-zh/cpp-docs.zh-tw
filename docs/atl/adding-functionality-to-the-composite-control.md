---
title: 將功能加入至複合控制項
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 9ad7ef3d80579804ac614fbefac1a042a9cf2fba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252490"
---
# <a name="adding-functionality-to-the-composite-control"></a>將功能加入至複合控制項

一旦您已將任何必要的控制項插入複合控制項下, 一個步驟牽涉到新增的新功能。 這項新功能通常會分成兩類：

- 支援的其他介面，並自訂您的複合控制項，與其他的特定功能的行為。

- 處理從包含 ActiveX 控制項 （或控制項） 的事件。

目的及本文的範圍中，本節的其餘部分著重於從 ActiveX 控制項中處理事件。

> [!NOTE]
>  如果您需要處理從 Windows 控制項的訊息，請參閱[實作視窗](../atl/implementing-a-window.md)如需有關在 ATL 中處理的訊息

之後插入 ActiveX 控制項對話方塊資源，以滑鼠右鍵按一下控制項，然後按一下**加入事件處理常式**。 選取您想要處理，並按一下 的事件**新增和編輯**。 事件處理常式程式碼會加入至控制項的.h 檔案。

複合控制項上的 ActiveX 控制項連接點會自動連線及中斷連線透過呼叫[CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。

## <a name="see-also"></a>另請參閱

[複合控制項基本概念](../atl/atl-composite-control-fundamentals.md)
