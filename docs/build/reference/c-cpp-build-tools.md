---
title: 其他 MSVC Build 工具
ms.date: 08/28/2019
f1_keywords:
- c.build
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
ms.openlocfilehash: 53c7c2f8c162cd851b4612e75ba14b019d9cbd63
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177290"
---
# <a name="additional-msvc-build-tools"></a>其他 MSVC Build 工具

Visual Studio 提供下列命令列公用程式來查看或操作組建輸出:

- [LIB。EXE](lib-reference.md)是用來建立和管理通用物件檔案格式 (COFF) 物件檔案的程式庫。 它也可以用來建立匯出檔案和匯入程式庫, 以參考匯出的定義。

- [EDITBIN。EXE](editbin-reference.md)是用來修改 COFF 二進位檔案。

- [DUMPBIN。EXE](dumpbin-reference.md)會顯示關於 COFF 二進位檔案的資訊 (例如符號表)。

- [NMAKE](nmake-reference.md)讀取並執行 makefile。

- [ERRLOOK](value-edit-control.md), 錯誤查閱公用程式會根據輸入的值, 抓取系統錯誤訊息或模組錯誤訊息。

- [XDCMake](xdcmake-reference.md)。 用來處理原始程式碼檔案的工具, 這些檔案包含以 XML 標記標記的檔批註。

- [BSCMAKE。EXE](bscmake-reference.md) (僅針對回溯相容性而提供) 會建立流覽資訊檔 (.bsc), 其中包含程式中的符號 (類別、函式、資料、宏和類型) 的相關資訊。 您可以在開發環境中的 [流覽] 視窗中, 看到這項資訊。 (.Bsc 檔案也可以建立在開發環境中)。

Windows SDK 也有數個組建工具, 包括[RC。EXE](/windows/win32/menurc/resource-compiler), 編譯器會C++叫用它來編譯原生 Windows 資源, 例如對話方塊、屬性頁、點陣圖、字串資料表等等。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)<br/>
[裝飾名稱](decorated-names.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 連結器選項](linker-options.md)
