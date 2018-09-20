---
title: 一般類別設計原理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe64ee4d9e6fc678d97c3e9fe37a85e53807541
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416639"
---
# <a name="general-class-design-philosophy"></a>一般類別設計原理

Microsoft Windows 的設計是 c + + 語言變得熱門之前。 由於數千個應用程式使用 C 語言的 Windows 應用程式開發介面 (API)，就會維護該介面可預見的未來。 因此必須建置任何 c + + Windows 介面的程序的 C 語言 API 之上。 這可確保 c + + 應用程式將能夠與 C 應用程式並存。

Microsoft Foundation 類別庫是物件導向的介面，以符合以下的設計目標的 Windows:

- 大幅縮小努力為 Windows 撰寫的應用程式的詳細資訊。

- 能夠與 C 語言 API 的執行速度。

- 最小的程式碼大小的額外負荷。

- 直接呼叫任何 Windows C 函式的能力。

- 現有的 C 應用程式，以 c + + 轉換更輕鬆。

- 運用現有的基底的 C 語言 Windows 程式設計經驗的能力。

- 更易於使用比 c 與 c + + 的 Windows api

- 容易使用，但功能強大的抽象概念的複雜功能，例如 ActiveX 控制項、 資料庫支援、 列印、 工具列和狀態列。

- 可以有效地使用 c + + 語言功能的 c + + 的 Windows API，則為 true。

如需 MFC 程式庫設計的詳細資訊，請參閱：

- [應用程式架構](../mfc/application-framework.md)

- [與 C 語言 API 的關聯性](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

