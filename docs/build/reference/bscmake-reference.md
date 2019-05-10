---
title: BSCMAKE 參考
ms.date: 05/06/2019
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: 72ad297ee5a24bc0c7ffd3ed25959031d0b8a309
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220553"
---
# <a name="bscmake-reference"></a>BSCMAKE 參考

> [!WARNING]
> 雖然 BSCMAKE 仍隨著 Visual Studio 安裝，IDE 已不再使用它。 從 Visual Studio 2008 起，瀏覽和符號資訊會自動儲存在方案資料夾的 SQL Server .sdf 檔案中。

Microsoft Browse Information Maintenance Utility (BSCMAKE.EXE) 會自編譯期間建立的 .sbr 檔案建置瀏覽資訊檔 (.bsc)。 某些協力廠商工具使用的程式碼分析的.bsc 檔案。

建置您的程式時，可以為您的程式自動建立瀏覽資訊檔，使用 BSCMAKE 來建置檔案。 您不需要知道如何執行 BSCMAKE，如果您在 Visual Studio 開發環境中建立您的瀏覽資訊檔。 不過，您可能想要閱讀本主題，了解可用的選項。

如果您在開發環境之外建置程式，您仍然可以在環境中建立您可以檢查的自訂 .bsc。 對編譯期間建立的 .sbr 檔案執行 BSCMAKE。

> [!NOTE]
>  您可以啟動此工具只能從 Visual Studio 開發人員命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

本節包括下列主題：

- [建置瀏覽資訊檔：概觀](building-browse-information-files-overview.md)

- [建置.bsc 檔](building-a-dot-bsc-file.md)

- [BSCMAKE 命令列](bscmake-command-line.md)

- [BSCMAKE 命令檔](bscmake-command-file-response-file.md)

- [BSCMAKE 選項](bscmake-options.md)

- [BSCMAKE 結束代碼](bscmake-exit-codes.md)

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](c-cpp-build-tools.md)
