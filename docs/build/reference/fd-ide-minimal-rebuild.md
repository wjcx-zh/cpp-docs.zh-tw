---
title: /FD (IDE 最少重建)
ms.date: 04/08/2019
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: ac63b021dc0cb9ee5964af7fa2e168f710653979
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292870"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (IDE 最少重建)

**/FD**中的使用者只公開[命令列](command-line-property-pages.md)屬性頁的C++專案的**屬性頁**對話方塊。 可用，才是已被取代並關閉預設[/Gm （啟用最少重建）](gm-enable-minimal-rebuild.md)選項未選取。 **/FD**以外沒有作用，從開發環境。 **/FD**的輸出中未公開`cl /?`。

如果您未啟用之已被取代 **/Gm**中開發環境中，選項 **/FD**用。 **/FD**可確保.idb 檔有足夠的相依性資訊。 **/FD**僅供開發環境中，而且不應該用於從命令列或組建指令碼。

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
