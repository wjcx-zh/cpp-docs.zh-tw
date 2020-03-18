---
title: /FD (IDE 最少重建)
ms.date: 04/08/2019
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 896adcb97a259e6714cf23241424841456371491
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439814"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (IDE 最少重建)

**/Fd**只會C++在專案 [**屬性頁**] 對話方塊的 [[命令列](command-line-property-pages.md)] 屬性頁中公開給使用者。 只有在未選取 [已取代] 和 [預設的[/gm （啟用最少重建）](gm-enable-minimal-rebuild.md) ] 選項時，才可以使用它。 **/Fd**在開發環境中不會有任何作用。 **/Fd**不會在 `cl /?`的輸出中公開。

如果您未在開發環境中啟用已淘汰的 **/gm**選項，則會使用 **/fd** 。 **/Fd**會確保 .idb 檔案具有足夠的相依性資訊。 **/Fd**僅供開發環境使用，而且不應該從命令列或組建腳本中使用。

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
