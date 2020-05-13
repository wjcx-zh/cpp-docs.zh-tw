---
title: 建置瀏覽資訊檔：概觀
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: ffacb7aaf9ac1f7ad6fc4cf12ab479099dc57725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320676"
---
# <a name="building-browse-information-files-overview"></a>建置瀏覽資訊檔：概觀

> [!WARNING]
> 雖然 BSCMAKE 仍隨著 Visual Studio 安裝，IDE 已不再使用它。 從 Visual Studio 2008 起，瀏覽和符號資訊會自動儲存在方案資料夾的 SQL Server .sdf 檔案中。

要為符號瀏覽建立瀏覽資訊,編譯器會為專案中的每個源文件創建一個 .sbr 檔,然後為 BSCMAKE 創建。EXE 將 .sbr 檔案串聯到一個 .bsc 檔中。

生成 .sbr 和 .bsc 檔需要時間,因此 Visual Studio 默認關閉這些功能。 如果要瀏覽當前資訊,則必須打開瀏覽選項並再次生成專案。

使用[/FR](fr-fr-create-dot-sbr-file.md)或[/Fr](fr-fr-create-dot-sbr-file.md)告訴編譯器創建 .sbr 檔案。 要建立 .bsc 檔案,可以從命令列呼叫[BSCMAKE。](bscmake-command-line.md) 使用命令列中的 BSCMAKE 可以更精確地控制流覽資訊檔的操作。 有關詳細資訊,請參閱[BSCMAKE 參考](bscmake-reference.md)。

> [!TIP]
> 您可以打開 .sbr 檔產生,但關閉 .bsc 檔生成。 這提供了快速的生成,但也使您能夠通過打開 .bsc 檔生成和生成專案快速創建新的 .bsc 檔。

您可以通過減小 .bsc 檔案的大小來減少生成 .bsc 檔案所需的時間、記憶體和磁碟空間。

有關如何在開發環境中生成瀏覽器檔的資訊,請參閱[常規屬性頁(專案)。](general-property-page-project.md)

### <a name="to-create-a-smaller-bsc-file"></a>建立較小的 .bsc 檔案

1. 使用[BSCMAKE 命令列選項](bscmake-options.md)從瀏覽資訊檔中排除資訊。

1. 編譯或組裝時,在一個或多個 .sbr 檔中省略本地符號。

1. 如果物件檔不包含當前調試階段所需的資訊,則在重新生成流覽資訊檔時,請從 BSCMAKE 命令省略其 .sbr 檔。

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>將多個項目的瀏覽資訊合併到瀏覽器檔 (.bsc)

1. 要麼不要在項目級別生成 .bsc 檔,或者使用 .n 開關來防止 .sbr 檔被截斷。

1. 生成所有專案後,使用所有 .sbr 檔作為輸入運行 BSCMAKE。 可使用萬用字元。 例如,如果專案目錄 C:\X、C:_Y 和 C:Z 包含 .sbr 檔,並且希望將它們全部合併到一個 .bsc 檔中,則使用\\\*BSCMAKE C:\X .sbr\\\*C:Y .sbr\\\*C:\Z .sbr /o c:\whatever_directory\s.bsc 來構建組合的 .bsc 檔。

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](c-cpp-build-tools.md)<br/>
[BSCMAKE 參考](bscmake-reference.md)
