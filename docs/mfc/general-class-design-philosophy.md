---
title: 一般類別設計原理
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 4dfa11c73703f5f2d3d17f8278610d32178af679
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219615"
---
# <a name="general-class-design-philosophy"></a>一般類別設計原理

Microsoft Windows 多久的設計C++語言變得熱門。 由於數千個應用程式使用 C 語言的 Windows 應用程式開發介面 (API)，就會維護該介面可預見的未來。 任何C++Windows 介面必須因此建置程序的 C 語言 API 之上。 這可確保C++應用程式將能夠與 C 應用程式並存。

Microsoft Foundation 類別庫是物件導向的介面，以符合以下的設計目標的 Windows:

- 大幅縮小努力為 Windows 撰寫的應用程式的詳細資訊。

- 能夠與 C 語言 API 的執行速度。

- 最小的程式碼大小的額外負荷。

- 直接呼叫任何 Windows C 函式的能力。

- 轉換現有的 C 應用程式，以更輕鬆C++。

- 運用現有的基底的 C 語言 Windows 程式設計經驗的能力。

- 更易於使用的 Windows apiC++比使用 c。

- 容易使用，但功能強大的抽象概念的複雜功能，例如 ActiveX 控制項、 資料庫支援、 列印、 工具列和狀態列。

- 適用於的 Windows API，則為 true C++ ，可以有效地使用C++語言功能。

如需 MFC 程式庫設計的詳細資訊，請參閱：

- [應用程式架構](../mfc/application-framework.md)

- [與 C 語言 API 的關聯性](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
