---
title: 一般類別設計原理
ms.date: 11/04/2016
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: cfad635c2a826c6f57e2e1513d753a4083494dee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618774"
---
# <a name="general-class-design-philosophy"></a>一般類別設計原理

Microsoft Windows 是在 c + + 語言變得很熱門之前就設計的。 因為有數千個應用程式使用 C 語言 Windows 應用程式開發介面（API），所以該介面將會針對可預見的未來進行維護。 因此，任何 c + + Windows 介面都必須建立在程式 C 語言 API 之上。 這可確保 c + + 應用程式能夠與 C 應用程式並存。

MFC 程式庫是 Windows 的物件導向介面，符合下列設計目標：

- 大幅減少撰寫 Windows 應用程式的投入時間。

- 執行速度相當於 C 語言 API。

- 最小程式代碼大小額外負荷。

- 能夠直接呼叫任何 Windows C 函數。

- 更輕鬆地將現有的 C 應用程式轉換為 c + +。

- 能夠利用現有 C 語言的 Windows 程式設計經驗。

- 比起 C，更輕鬆地使用 Windows API （c + +）。

- 更容易使用複雜功能的強大抽象概念，例如 ActiveX 控制項、資料庫支援、列印、工具列和狀態列。

- 適用于 c + + 的 True Windows API，可有效地使用 c + + 語言功能。

如需 MFC 程式庫設計的詳細資訊，請參閱：

- [應用程式架構](application-framework.md)

- [與 C 語言 API 的關聯性](relationship-to-the-c-language-api.md)

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
