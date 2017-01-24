---
title: "XML 文件 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 文件的 /// 分隔符號"
  - "註解, C++ 原始程式碼檔"
  - "XML 文件"
  - "XML, 原始程式碼中的文件註解"
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# XML 文件 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual C\+\+ 中，您可以將註解加入至處理至 .xml 檔案的原始程式碼。  這個檔案可以是輸入到建立類別的文件程式碼的流程。  
  
 在 Visual C\+\+ 程式碼檔案， XML 必須直接在方法或型別定義之前位於文件註解。  註解在下列案例中可用來填入 Intellisense QuickInfo 資料提示:  
  
1.  編譯程式碼時，有隨附的 .winmd 檔案的 Windows 執行階段元件  
  
2.  當原始程式碼在目前中包含專案  
  
3.  在型別宣告和實作位於相同標頭檔的程式庫中。  
  
> [!NOTE]
>  在目前版本中，程式碼註解沒有處理包含範本類型 \(例如，函式的範本或任何使用參數做為範本\)。  將此註解產生未定義的行為。  
  
 如需建立 .xml 檔案的資料相關的文件註解的詳細資訊，請參閱下列主題。  
  
|如需下列資訊|請參閱|  
|------------|---------|  
|編譯器使用的選項。|[\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
|您可以使用所提供資料的常用功能的標記。|[建議的文件註解標記](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|  
|編譯器產生識別建構程式碼的 ID 字串|[處理 .xml 檔案](../ide/dot-xml-file-processing.md)|  
|如何分隔資料標記|[Visual C\+\+ 文件標記的符號](../ide/delimiters-for-visual-cpp-documentation-tags.md)|  
|產生 .xml 從一或多個 .xdc 檔案。|[XDCMake 參考](../ide/xdcmake-reference.md)|  
|資訊的連結至 XML，則會與 Visual Studio 功能區域相關。|[在 Visual Studio 中的 XML](../Topic/XML%20Tools%20in%20Visual%20Studio.md)|  
  
 如果您需要將 XML 文件的文字的特性註解，您必須使用 XML 實體或 CDATA 區段。  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)