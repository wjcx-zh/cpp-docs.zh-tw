---
title: 建置瀏覽資訊檔：總覽
ms.date: 11/04/2016
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 4f12bd25ca3ab718a845dbb04aba3169cc6d4b19
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820601"
---
# <a name="building-browse-information-files-overview"></a>建置瀏覽資訊檔：總覽

若要建立的符號瀏覽資訊，編譯器會建立每個原始程式檔的.sbr 檔案，在您的專案，然後 BSCMAKE。EXE 會串連成一個.bsc 檔案的.sbr 檔案。

讓 Visual c + + 會關閉這些函式，根據預設，產生.sbr 和.bsc 檔案需要時間。 如果您想要瀏覽目前的資訊，您必須開啟的瀏覽選項，並再次建置您的專案。

使用[/FR](fr-fr-create-dot-sbr-file.md)或是[/Fr](fr-fr-create-dot-sbr-file.md)告訴編譯器建立.sbr 檔案。 若要建立.bsc 檔案，您可以呼叫[BSCMAKE](bscmake-command-line.md)從命令列。 從命令列使用 BSCMAKE，讓您更精確地控制瀏覽資訊檔的操作。 請參閱[BSCMAKE 參考](bscmake-reference.md)如需詳細資訊。

> [!TIP]
>  您可以開啟產生的.sbr 檔，但保留已關閉的.bsc 檔產生。 這提供快速的組建，但也可讓您藉由開啟產生的.bsc 檔及建置專案，快速建立新的.bsc 檔。

您可以減少時間、 記憶體和磁碟空間才能建置.bsc 檔藉由減少.bsc 檔的大小。

請參閱[一般屬性頁 （專案）](general-property-page-project.md)如需有關如何建立開發環境中的瀏覽器檔案資訊。

### <a name="to-create-a-smaller-bsc-file"></a>若要建立較小的.bsc 檔案

1. 使用[BSCMAKE 命令列選項](bscmake-options.md)以排除瀏覽資訊檔的資訊。

1. 略過一或多個.sbr 檔時編譯或組合中的本機符號。

1. 如果物件檔案沒有您的偵錯的目前階段所需的資訊，請省略 BSCMAKE 命令從其.sbr 檔，當您重建瀏覽資訊檔。

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>若要瀏覽資訊結合數個專案成一個瀏覽器檔 (.bsc)

1. 不建置.bsc 檔在專案層級或使用 /n 參數來防止.sbr 檔被截斷。

1. 建置所有專案之後，請使用所有.sbr 檔案都執行 BSCMAKE，做為輸入。 使用萬用字元。 比方說，如果您有使用.sbr 檔，以及您想要將它們結合成一個.bsc 檔案，所有 C:\X、 C:\Y 和 C:\Z 的專案目錄，然後使用 BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\\*.sbr /o c:\whatever_directory\combined.bsc 建置結合的.bsc 檔案。

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](c-cpp-build-tools.md)<br/>
[BSCMAKE 參考](bscmake-reference.md)
