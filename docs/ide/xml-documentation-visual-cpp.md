---
title: XML 文件 （Visual c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee19c51c04fa32ab3c2f1810bb963b22ec7e890
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xml-documentation-visual-c"></a>XML 文件 (Visual C++)
Visual c + + 中，您可以註解加入至.xml 檔案將會處理的原始程式碼中。 這個檔案接著可以在您的程式碼中建立類別的文件的程序的輸入。  
  
 在 Visual c + + 程式碼檔案中，必須直接在方法或類型定義之前位於 XML 文件註解。 註解可以用來填入 Intellisense QuickInfo 資料提示方塊，在下列案例：  
  
1.  當程式碼會編譯為 Windows 執行階段元件與隨附的.winmd 檔案  
  
2.  當目前的專案中隨附的原始程式碼  
  
3.  文件庫中的型別宣告和實作位於相同的標頭檔  
  
> [!NOTE]
>  在目前版本中，程式碼註解不會處理範本，或包含範本類型 （例如，函式做為範本參數） 的任何項目上。 新增這類的註解，將會導致未定義的行為。  
  
 如需與文件註解建立的.xml 檔案的詳細資訊，請參閱下列主題。  
  
|如需以下相關資訊|請參閱|  
|---------------------------|---------|  
|要使用的編譯器選項|[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
|您可以使用提供常用的標記文件中使用的功能|[建議使用的文件註解標籤](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|  
|編譯器會產生以識別您的程式碼中建構的識別碼字串|[處理的.xml 檔案](../ide/dot-xml-file-processing.md)|  
|如何分隔文件標記|[Visual C++ 文件標記的分隔符號](../ide/delimiters-for-visual-cpp-documentation-tags.md)|  
|從一或多個.xdc 檔中產生的.xml 檔案。|[XDCMake 參考](../ide/xdcmake-reference.md)|  
|如同 XML 的相關資訊的連結與 Visual Studio 功能區|[Visual Studio 中的 XML](/visualstudio/xml-tools/xml-tools-in-visual-studio)|  
  
 如果您需要將 XML 特殊字元放在文件註解的文字，您必須使用 XML 實體區段或 CDATA 區段。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)