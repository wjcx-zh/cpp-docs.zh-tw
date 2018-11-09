---
title: XML 文件 (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: 380fe73bba71d08bb9315e218f5946a7cf935108
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523882"
---
# <a name="xml-documentation-visual-c"></a>XML 文件 (Visual C++)

在 Visual C++ 中，您可以將註解新增至將處理為 .xml 檔案的原始程式碼。 這個檔案便可以成為針對您程式碼中的類別建立文件之程序的輸入。

在 Visual C++ 程式碼檔案中，XML 文件註解必須直接位於方法或型別定義之前。 註解可以在下列案例中用來填入 IntelliSense QuickInfo 資料提示方塊：

1. 當程式碼編譯為 Windows 執行階段元件與隨附的 .winmd 檔案

1. 當目前專案中包含原始程式碼

1. 在型別宣告和實作位於相同標頭檔中的程式庫

> [!NOTE]
>  在目前版本中，在範本或包含範本類型的任何項目上 (例如，以範本形式接受參數的函式) 不會處理程式碼註解。 新增這類的註解，將會導致未定義的行為。

如需建立具有文件註解 .xml 檔案的詳細資料，請參閱下列主題。

|如需以下相關資訊|請參閱|
|---------------------------|---------|
|要使用的編譯器選項|[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|
|您可以用來在文件中提供常用功能的標記|[建議使用的文件註解標籤](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|
|編譯器會產生以識別您程式碼中之建構的識別碼字串|[處理 .xml 檔案](../ide/dot-xml-file-processing.md)|
|如何分隔文件標記|[Visual C++ 文件標記的分隔符號](../ide/delimiters-for-visual-cpp-documentation-tags.md)|
|從一或多個 .xdc 檔產生 .xml 檔。|[XDCMake 參考](../ide/xdcmake-reference.md)|
|XML 與 Visual Studio 功能區之關聯性的資訊連結|[Visual Studio 中的 XML](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

如果您需要將 XML 特殊字元放在文件註解的文字裡，必須使用 XML 實體或 CDATA 區段。

## <a name="see-also"></a>請參閱

[執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)