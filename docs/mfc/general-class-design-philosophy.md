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
ms.openlocfilehash: 34a173802e3fa43615c05da4ce747592f851228f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441196"
---
# <a name="general-class-design-philosophy"></a>一般類別設計原理

Microsoft Windows 的設計是在C++語言變得很熱門之前。 因為有數千個應用程式使用 C 語言 Windows 應用程式開發介面（API），所以該介面將會針對可預見的未來進行維護。 因此C++ ，任何 Windows 介面都必須建立在程式 C 語言 API 之上。 這可確保C++應用程式能夠與 C 應用程式並存。

MFC 程式庫是 Windows 的物件導向介面，符合下列設計目標：

- 大幅減少撰寫 Windows 應用程式的投入時間。

- 執行速度相當於 C 語言 API。

- 最小程式代碼大小額外負荷。

- 能夠直接呼叫任何 Windows C 函數。

- 更輕鬆地將現有的 C C++應用程式轉換成。

- 能夠利用現有 C 語言的 Windows 程式設計經驗。

- C++比起 C，更容易使用 Windows API。

- 更容易使用複雜功能的強大抽象概念，例如 ActiveX 控制項、資料庫支援、列印、工具列和狀態列。

- 適用于C++的 TRUE Windows API 可C++有效地使用語言功能。

如需 MFC 程式庫設計的詳細資訊，請參閱：

- [應用程式架構](../mfc/application-framework.md)

- [與 C 語言 API 的關聯性](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)
