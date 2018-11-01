---
title: 網際網路安全性 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
ms.openlocfilehash: e7892793a82f2b030a99465a712e33e1b9ef4673
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486095"
---
# <a name="internet-security-c"></a>網際網路安全性 (C++)

程式碼安全性是開發人員和使用者的網際網路應用程式的主要問題。 有風險： 惡意程式碼、 程式碼已遭竄改，以及從不明的網站] 或 [作者的程式碼。

開發網際網路時，有兩種安全性的基本方法。 第一個部分稱為 「 沙箱 」。 這種方法，是限制為一組特定的 Api，應用程式，並將其排除等檔案 I/O，程式無法終結使用者的電腦上的資料有潛在危險的項目中。 第二個是使用數位簽章來實作。 這種方法稱為 「 shrinkwrap 」 的網際網路功能。 程式碼會驗證，並使用私密金鑰/公開金鑰的關鍵技術簽章。 在執行的程式碼之前，以確保程式碼是從已知的驗證來源，而且，程式碼未被改變已簽署之後驗證其數位簽章。

在第一個案例中，您可以信任應用程式將不會做任何傷害，以及您信任來源的應用程式。 在第二個，數位簽章來確認真實性。 數位簽章是一項工業標準，其用來識別，並提供程式碼的 「 發行者 」 的詳細資料。 其技術是以標準，包括 RSA 和 X.509 為基礎。 瀏覽器通常會允許使用者選擇是否要下載及執行未知來源的程式碼。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)

