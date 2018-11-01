---
title: 建立 .Sbr 檔
ms.date: 11/04/2016
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
ms.openlocfilehash: 63f007e567f3c1db556ba6a7f0c1a354c449f31b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500996"
---
# <a name="creating-an-sbr-file"></a>建立 .Sbr 檔

BSCMAKE 的輸入的檔是.sbr 檔案。 編譯器會建立.sbr 檔案以供編譯每個目的檔 (.obj)。 當您建立或更新您的瀏覽資訊檔時，為您的專案的所有.sbr 檔必須都是在磁碟上使用。

若要建立的.sbr 檔案與所有可能的資訊，請指定[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)。

若要建立的.sbr 檔案中不含本機符號，指定[/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)。 如果的.sbr 檔案包含本機符號，您可以仍然從省略.bsc 檔使用 BSCMAKE 的[/El 選項](../../build/reference/bscmake-options.md)`.`

您可以建立的.sbr 檔案，而不執行完整的編譯。 例如，您可以在其中指定 /Zs 選擇編譯器執行語法檢查，並仍產生的.sbr 檔案，如果您指定 /FR 的話。

建置程序可能更有效率，如果的.sbr 檔案會先封裝以移除未參考的定義。 編譯器會自動套件.sbr 檔案。

## <a name="see-also"></a>另請參閱

[建置 .Bsc 檔](../../build/reference/building-a-dot-bsc-file.md)