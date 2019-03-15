---
title: /FD (IDE 最少重建)
ms.date: 11/04/2016
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 323a0045ab11f23ab996d5179a135d0eb4184f20
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817435"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (IDE 最少重建)

**/FD**不會公開給使用者，除了在[命令列](command-line-property-pages.md)c + + 專案的屬性頁**屬性頁**對話方塊中，如果且只有[/Gm (啟用最少重建）](gm-enable-minimal-rebuild.md)也未選取。 **/FD**以外沒有作用，從開發環境。 **/FD**的輸出中未公開**cl /？**。

如果您未啟用 **/Gm**在開發環境中， **/FD**將使用。 **/FD**可確保.idb 檔具有足夠的相依性資訊。 **/FD**僅供開發環境中，而且不應該用於從命令列或組建指令碼。

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
