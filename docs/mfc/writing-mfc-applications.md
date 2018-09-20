---
title: 撰寫 MFC 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet applications [MFC], MFC
- MFC, Internet applications
- application wizards [MFC], Internet applications
- MFC, application development
ms.assetid: 6a8d8a03-abfa-4976-86c2-c5773a4b7179
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2bb5cfa0653f7072cc9e968a8db1d5d1a48e445
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385751"
---
# <a name="writing-mfc-applications"></a>撰寫 MFC 應用程式

這篇文章說明您需要開發您的應用程式的初始步驟。 首先，您必須決定您要撰寫的應用程式種類。 有幾個選項中已討論過[應用程式設計選擇](../mfc/application-design-choices.md)。 您的應用程式會：

- 在網際網路或近端內部網路上執行

- 在用戶端或伺服器上執行

- 在瀏覽器中，或是獨立的應用程式執行

- 使用 COM 或 Active 技術

- 使用 WinInet 或非同步 moniker 下載資料

您的決策會判斷哪些類別是適用於您的應用程式。 您的答案也有助於判斷您執行應用程式精靈，開始建構您的應用程式時所做的選取項目。

關於網際網路應用程式進行最初的設計決策之後，您可以使用應用程式精靈 來開始。 您可以使用應用程式精靈 來建立基本架構的應用程式，並修改程式碼，如下列文章中所述：

- ActiveX 控制項，請參閱[網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)。

下列文件也會提供指示來協助您開始您的程式設計工作：

- [應用程式設計選擇](../mfc/application-design-choices.md)

- [網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)

- [WinInet 基本概念](../mfc/wininet-basics.md)

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)

