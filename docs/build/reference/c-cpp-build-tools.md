---
title: 其他 MSVC 建置工具
ms.date: 05/06/2019
f1_keywords:
- c.build
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
ms.openlocfilehash: 59c9cb4527de878b06cbb6a7b3abe921e9a60107
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220214"
---
# <a name="additional-msvc-build-tools"></a>其他 MSVC 建置工具

Visual Studio 提供下列的命令列公用程式來檢視或操作組建輸出：


- [LIB。EXE](lib-reference.md)用來建立及管理通用物件檔案格式 (COFF) 物件檔的程式庫。 它也可以用來建立匯出檔案和程式庫匯入參考匯出的定義。

- [EDITBIN。EXE](editbin-reference.md)用來修改 COFF 二進位檔。

- [DUMPBIN。EXE](dumpbin-reference.md)顯示資訊 COFF 二進位檔案 （例如符號資料表）。

- [NMAKE](nmake-reference.md)讀取並執行 makefile。

- [ERRLOOK](value-edit-control.md)，錯誤查詢公用程式會擷取系統錯誤訊息或輸入的值為基礎的模組錯誤訊息。

- [XDCMake](xdcmake-reference.md)。 Toolfor，處理原始程式碼檔案包含文件註解標示的 XML 標記。

- [BSCMAKE。EXE](bscmake-reference.md) （基於回溯相容性提供） 建置瀏覽資訊檔 (.bsc)，其中包含您的程式中的符號 （類別、 函式、 資料、 巨集和類型） 的相關資訊。 您在開發環境內的瀏覽 視窗中檢視這項資訊。 （.bsc 檔可以也是建置在開發環境中）。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)<br/>
[裝飾名稱](decorated-names.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 連結器選項](linker-options.md)
