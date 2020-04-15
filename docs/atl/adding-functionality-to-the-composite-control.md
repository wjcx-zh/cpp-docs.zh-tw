---
title: 新增組合的控制項
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 5de18f863831973af384d2456adb5b2214f0dd68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317418"
---
# <a name="adding-functionality-to-the-composite-control"></a>新增組合的控制項

將任何必要的控制項插入到複合控制項中後,下一步將添加新功能。 此新功能通常分為兩類:

- 支援其他介面,並自定義複合控制項的行為與其他特定功能。

- 從包含的 ActiveX 控制件(或控制項)處理事件。

就本文的目的和範圍而言,本節的其餘部分僅側重於處理來自 ActiveX 控件的事件。

> [!NOTE]
> 如果需要處理來自 Windows 控件的消息,請參閱[實現視窗](../atl/implementing-a-window.md),瞭解有關 ATL 中郵件處理的詳細資訊。

在對話框資源中插入 ActiveX 控制項後,右鍵按一下該控制項並按下「**添加事件處理程式**」 。。 選擇要處理的事件,然後按下「**添加和編輯**」。 事件處理程式代碼將添加到控制項的 .h 檔中。

複合控制的 ActiveX 控制項的連線點來透過[電話連線的 CCom 複合控制系統自動連線與斷線連接::建議SinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。

## <a name="see-also"></a>另請參閱

[複合控制項基本概念](../atl/atl-composite-control-fundamentals.md)
