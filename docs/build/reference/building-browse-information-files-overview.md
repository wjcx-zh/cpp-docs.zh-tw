---
title: 建置瀏覽資訊檔：概觀
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 94cb5865e56e12f51ef4a8598a5df3fcbe69fa0f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078351"
---
# <a name="building-browse-information-files-overview"></a>建置瀏覽資訊檔：概觀

> [!WARNING]
> 雖然 BSCMAKE 仍隨著 Visual Studio 安裝，IDE 已不再使用它。 從 Visual Studio 2008 起，瀏覽和符號資訊會自動儲存在方案資料夾的 SQL Server .sdf 檔案中。

若要建立符號流覽的流覽資訊，編譯器會為專案中的每個原始程式檔建立一個 .sbr 檔案，然後為 BSCMAKE。EXE 會將 .sbr 檔案串連成一個 .bsc 檔案。

產生 .sbr 和 .bsc 檔案需要一些時間，因此 Visual Studio 預設會關閉這些功能。 如果您想要流覽目前的資訊，您必須開啟 [流覽] 選項，然後再次建立您的專案。

使用[/fr](fr-fr-create-dot-sbr-file.md)或[/fr](fr-fr-create-dot-sbr-file.md)來指示編譯器建立 .sbr 檔案。 若要建立 .bsc 檔案，您可以從命令列呼叫[BSCMAKE](bscmake-command-line.md) 。 從命令列使用 BSCMAKE，可讓您更精確地控制流覽資訊檔案的操作。 如需詳細資訊，請參閱[BSCMAKE 參考](bscmake-reference.md)。

> [!TIP]
>  您可以開啟 .sbr 檔案產生，但將 .bsc 檔案產生保持關閉。 這會提供快速組建，但也可讓您快速建立新的 .bsc 檔案，方法是開啟 .bsc 檔案產生並建立專案。

藉由減少 .bsc 檔案的大小，您可以減少建立 .bsc 檔案所需的時間、記憶體和磁碟空間。

如需如何在開發環境中建立瀏覽器檔案的詳細資訊，請參閱[一般屬性頁（專案）](general-property-page-project.md) 。

### <a name="to-create-a-smaller-bsc-file"></a>建立較小的 .bsc 檔案

1. 使用[BSCMAKE 命令列選項](bscmake-options.md)，從流覽資訊檔案中排除資訊。

1. 編譯或組合時，請省略一或多個 .sbr 檔案中的區域符號。

1. 如果物件檔案不包含您目前的偵錯工具階段所需的資訊，當您重建流覽資訊檔案時，請從 BSCMAKE 命令中省略其 .sbr 檔案。

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>將數個專案的流覽資訊合併成一個瀏覽器檔案（.bsc）

1. 請不要在專案層級建立 .bsc 檔案，或使用/n 參數防止 .sbr 檔被截斷。

1. 建立所有專案之後，請執行 BSCMAKE 並將所有 .sbr 檔案當做輸入。 可使用萬用字元。 例如，如果您有專案目錄 C:\X、C:\Y 和 C:\Z，而且您想要將它們全部結合成一個 .bsc 檔案，那麼請使用 BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\\*\combined.bsc 來建立結合的 .bsc 檔案。

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](c-cpp-build-tools.md)<br/>
[BSCMAKE 參考](bscmake-reference.md)
