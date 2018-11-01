---
title: 測試網際網路應用程式
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
ms.openlocfilehash: 934d336f8c7544bafa412a7b52404a657e8dc9ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439360"
---
# <a name="testing-internet-applications"></a>測試網際網路應用程式

在網際網路上有一些獨一無二的測試挑戰，特別是在 Web 伺服器上執行的應用程式。 您的初始測試可能會使用單一使用者的用戶端連接到測試伺服器來進行。 這對於偵錯您的程式碼將會非常有用。

您也會想要在實際的情況下進行測試：有多個用戶端透過高速連線進以及低速線路進行連接，包括數據機連接。 模擬真實的情況非常困難，不過仍值得花時間設計可能的情況並執行它們。 可能的話，您可能也會想要使用工具進行產能和壓力測試。 某些 Bug 的類別 (例如計時 Bug) 很難尋找並重新產生。

網際網路程式設計的其中一個挑戰就在於其可視性。 對網站的許多存取可能會降低伺服器的速度。 您會希望伺服器緩慢地降低效能。 如果您的應用程式失敗 (例如，寫入登錄或是在用戶端寫入 Cookie 時資料損毀)，您要避免發生可能會對使用者的電腦造成破壞性的任何事情。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)

