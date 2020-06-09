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
ms.openlocfilehash: ce044014c5c2e13528cea8b982227b0ec8bc03fc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621529"
---
# <a name="internet-security-c"></a>網際網路安全性 (C++)

程式碼安全性是開發人員和網際網路應用程式使用者的主要問題。 有風險：惡意程式碼、已遭篡改的程式碼，以及來自不明網站或作者的程式碼。

針對網際網路進行開發時，有兩種基本的安全性方法。 第一個稱為「沙箱」。 在此方法中，應用程式會限制為一組特定的 Api，並排除在可能危險的情況下（例如，檔案 i/o，程式可能會損毀使用者電腦上的資料）。 第二個會使用數位簽章來執行。 這種方法稱為網際網路的「shrinkwrap」。 使用私密金鑰/公開金鑰技術來驗證和簽署程式碼。 在執行程式碼之前，會驗證其數位簽章，以確保程式碼來自已知的已驗證來源，而且程式碼在簽署後並未改變。

在第一種情況下，您信任應用程式不會有任何傷害，而且您信任應用程式的來源。 在第二個中，數位簽章是用來驗證真實性。 數位簽章是一種業界標準，用來識別和提供有關程式碼發行者的詳細資料。 其技術是以標準為基礎，包括 RSA 和 x.509。 瀏覽器通常可讓使用者選擇是否要下載及執行不明來源的程式碼。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](mfc-internet-programming-basics.md)
