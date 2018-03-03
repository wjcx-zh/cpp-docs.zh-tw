---
title: "撰寫及重構程式碼 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b68d4190d8e3fc5040879eba4f8888467a07adf5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="writing-and-refactoring-code-c"></a>撰寫及重構程式碼 (C++)

Visual C++ 程式碼編輯器和 IDE 提供許多程式碼撰寫的輔助工具。 有些是 C++ 獨有，有些則基本上對所有 Visual Studio 語言都相同。 如需共用功能的詳細資訊，請參閱[程式碼和文字編輯器中撰寫程式碼](/visualstudio/ide/writing-code-in-the-code-and-text-editor)。 啟用及設定 c + + 特有功能的選項都位於[文字編輯器 c + + 進階](/visualstudio/ide/reference/options-text-editor-c-cpp-advanced)對話方塊 (**工具 &#124;選項 &#124;文字編輯器 &#124;C/c + + &#124;進階**或輸入 「 c + + 進階 」**快速啟動**)。 選擇您想要設定哪一個的選項之後，您可以取得更多說明按**F1**對話方塊顯示時。 對於一般程式碼格式設定選項，輸入`Editor C++`到**Environment**。

實驗功能，這可能或可能不會包含在 Visual Studio 的未來版本中，位於[文字編輯器 c + + 實驗](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental)對話方塊。 您可以啟用在 Visual Studio 2017**預測 Intellisense**在這個對話方塊中。

## <a name="adding-new-code"></a>加入新的程式碼

建立專案之後，您可以開始在為您所產生的檔案中撰寫程式碼。 若要加入新的檔案，以滑鼠右鍵按一下方案總管] 中的專案節點，然後選擇 [**新增 &#124;新**。

若要設定格式選項，例如縮排、 大括號完成和顏色標示，請輸入`C++ Formatting`到**Environment**視窗。

### <a name="intellisense"></a>IntelliSense

IntelliSense 是一組功能的名稱，提供有關成員、類型和函式多載的內嵌資訊。 下圖顯示您在輸入時會出現的下拉式成員清單。 您可以按下 [tab] 鍵，將選取的項目文字輸入到您的程式碼檔案。

![C# 43; &#43;成員下拉式清單](../ide/media/vs2015_cpp_statement_completion.png "vs2015_cpp_statement_completion")

如需完整資訊，請參閱[Visual c + + Intellisense](/visualstudio/ide/visual-cpp-intellisense)。

### <a name="insert-snippets"></a>插入程式碼片段

程式碼片段是預先定義的原始碼片段。 以滑鼠右鍵按一下單點或選取的文字，可插入程式碼片段或以程式碼片段圍繞選取的文字。 下圖顯示以 for 迴圈圍繞所選陳述式的三個步驟。 最終影像中的黃色反白顯示就是您使用 tab 鍵存取的可編輯欄位。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。

![Visual C# 43; &#43;插入程式碼片段卸除 &#45; 向下](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

### <a name="add-class"></a>加入類別

加入新的類別從**專案**功能表使用 類別精靈。

![在 Visual C# 43; &#43; 加入新的類別] (../ide/media/vs2015_cpp_add_class.png "vs2015_cpp_add_class")

### <a name="class-wizard"></a>類別精靈

使用 [類別精靈] 修改或檢查現有的類別，或加入新的類別。 如需詳細資訊，請參閱[加入功能與程式碼精靈 （c + +）](../ide/adding-functionality-with-code-wizards-cpp.md)。

![Visual C# 43; &#43;類別精靈](../ide/media/vs2015_cpp_class_wizard.png "vs2015_cpp_class_wizard")

## <a name="refactoring"></a>重構

重構功能，可在 [快速動作] 內容功能表中，或是按一下[燈泡](/visualstudio/ide/perform-quick-actions-with-light-bulbs)在編輯器中。  部分也存在於**編輯 > 重構**功能表。  這些功能包括：

* [重新命名](refactoring/rename.md)
* [擷取函式](refactoring/extract-function.md)
* [實作純虛擬函式](refactoring/implement-pure-virtuals.md)
* [建立宣告/定義](refactoring/create-declaration-definition.md)
* [移動函式定義](refactoring/move-definition-location.md)
* [轉換為原始字串常值](refactoring/convert-to-raw-string-literal.md)
* [變更簽章](refactoring/change-signature.md)

## <a name="navigate-and-understand"></a>巡覽和了解

Visual c + + 與其他語言共用許多程式碼巡覽功能。 如需詳細資訊，請參閱[導覽程式碼](/visualstudio/ide/navigating-code)和[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。

### <a name="quickinfo"></a>QuickInfo

將滑鼠暫留在變數上，可檢視其類型資訊。

![Visual C&#43;&#43; 快速諮詢](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

### <a name="open-document-navigate-to-header"></a>開啟文件 (巡覽至標頭)

在 `#include` 指示詞中的標頭名稱上按一下滑鼠右鍵，並開啟標頭檔。

![Visual C# 43; &#43;開啟文件功能表選項](../ide/media/vs2015_cpp_open_document.png "vs2015_cpp_open_document")

### <a name="peek-definition"></a>查看定義

將滑鼠停留在變數或函式宣告，以滑鼠右鍵按一下，然後選擇 **查看定義**以查看其定義的內嵌檢視。 如需詳細資訊，請參閱[查看定義 (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12)。

![Visual C# 43; &#43;查看定義](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

### <a name="go-to-definition"></a>移至定義

將滑鼠停留在變數或函式宣告，以滑鼠右鍵按一下，然後選擇 **移至定義**開啟文件的物件定義的位置。

### <a name="view-call-hierarchy"></a>檢視呼叫階層

以滑鼠右鍵按一下任何函式呼叫，並檢視它呼叫的所有函式 (以及呼叫它的所有函式) 之遞迴清單。 清單中的每個函式都可以用相同方式展開。 如需詳細資訊，請參閱[呼叫階層](/visualstudio/ide/reference/call-hierarchy)。

![Visual C# 43; &#43;呼叫階層](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

### <a name="toggle-header--code-file"></a>切換標頭/程式碼檔

以滑鼠右鍵按一下，然後選擇 **切換標頭 / 程式碼檔案**標頭檔和其相關聯的程式碼檔案之間來回切換。

### <a name="outlining"></a>大綱

原始程式碼檔中的任何位置按一下滑鼠右鍵，然後選擇 **大綱**摺疊或展開定義和/或自訂區域，讓您更輕鬆地瀏覽您感興趣的組件。 如需詳細資訊，請參閱[大綱](/visualstudio/ide/outlining)。

![Visual C# 43; &#43;大綱](../ide/media/vs2015_cpp_outlining.png "vs2015_cpp_outlining")

### <a name="scroll-bar-map-mode"></a>捲軸對應模式

捲軸對應模式可讓您快速地捲動及瀏覽程式碼檔案，而不需要實際離開目前位置。 或按一下 Code Map 上的任何位置，直接移至該處。

![Visual C# 43; &#43; 中的 code Map] (../ide/media/vs2015_cpp_code_map.png "vs2015_cpp_code_map")

### <a name="generate-graph-of-include-files"></a>產生 Include 檔圖形

在您的專案中的程式碼檔案上按一下滑鼠右鍵，然後選擇 **產生 include 檔圖形**，查看的圖形，其中檔案被包含的其他檔案。

![Visual C# 43; &#43;include 檔圖形](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

### <a name="f1-help"></a>F1 說明

將游標放在任何類型、關鍵字或函式之處或之後，然後按 [F1] 鍵即可直接跳到相關的 MSDN 參考主題。 F1 鍵也適用於錯誤清單中及許多對話方塊中的項目。

### <a name="quick-launch"></a>快速啟動

若要輕鬆地巡覽至 Visual Studio 中的任何視窗或工具，只要在 UI 右上角的 [快速啟動] 視窗中輸入其名稱即可。 當您輸入時，就會篩選自動完成清單。

![Visual Studio 快速啟動](../ide/media/vs2015_cpp_quick_launch.png "vs2015_cpp_quick_launch")
