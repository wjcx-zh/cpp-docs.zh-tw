---
title: 建立。Sbr 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac872dd13458c3fe15971f30a72b06e5510c5bd0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723680"
---
# <a name="creating-an-sbr-file"></a>建立 .Sbr 檔

BSCMAKE 的輸入的檔是.sbr 檔案。 編譯器會建立.sbr 檔案以供編譯每個目的檔 (.obj)。 當您建立或更新您的瀏覽資訊檔時，為您的專案的所有.sbr 檔必須都是在磁碟上使用。

若要建立的.sbr 檔案與所有可能的資訊，請指定[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)。

若要建立的.sbr 檔案中不含本機符號，指定[/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)。 如果的.sbr 檔案包含本機符號，您可以仍然從省略.bsc 檔使用 BSCMAKE 的[/El 選項](../../build/reference/bscmake-options.md)`.`

您可以建立的.sbr 檔案，而不執行完整的編譯。 例如，您可以在其中指定 /Zs 選擇編譯器執行語法檢查，並仍產生的.sbr 檔案，如果您指定 /FR 的話。

建置程序可能更有效率，如果的.sbr 檔案會先封裝以移除未參考的定義。 編譯器會自動套件.sbr 檔案。

## <a name="see-also"></a>另請參閱

[建置 .Bsc 檔](../../build/reference/building-a-dot-bsc-file.md)