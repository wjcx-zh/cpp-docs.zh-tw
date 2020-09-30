---
title: 用於升級 c + + 程式碼 Visual Studio IDE 工具
description: Visual Studio 的 c + + 程式碼編輯器和程式碼分析工具，可協助您將 c + + 程式碼基底現代化。
ms.date: 11/13/2019
ms.topic: conceptual
ms.openlocfilehash: d6368445d16232ff968b7116b0f0313e97aa144c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503765"
---
# <a name="visual-studio-ide-tools-for-upgrading-c-code"></a>用於升級 c + + 程式碼 Visual Studio IDE 工具

Visual Studio 可協助您使用編譯器選項、程式碼分析警告和編輯器功能（例如快速修正、快速諮詢和增強的捲軸）來升級舊版 c + + 程式碼。 「舊版程式碼」一詞是指下列任何類別：

- Microsoft c + + 編譯器先前允許的程式碼 (MSVC) 但永遠不符合 c + + 標準。

   若要升級舊版不一致的 MSVC 程式碼，請開啟 [/permissive-](../build/reference/permissive-standards-conformance.md) 編譯器選項。 在程式碼編輯器中，所有不一致使用方式的實例會加上紅色波浪線。 [ **錯誤清單** ] 視窗中的錯誤訊息包含如何修正錯誤的建議。 按一下錯誤碼以移至檔中的說明頁面。 如果一次修正所有錯誤，您可以藉由開啟寬鬆選項、修正某些錯誤，然後再次關閉該選項，在階段升級不一致的 **程式** 代碼。 程式碼會以新的改進進行編譯，您可以稍後再返回並修正其餘的問題。 如需不一致 MSVC 程式碼的範例，請參閱 [/permissive-](../build/reference/permissive-standards-conformance.md) 頁面。

- 舊版 c + + 標準中允許的程式碼，但在較新版本中已被取代或移除。

   若要升級至較新的語言標準，請將 [c + + 語言標準](../build/reference/std-specify-language-standard-version.md) 選項設定為所需的標準，並修正任何引發的編譯錯誤。 一般情況下，我們建議將語言標準設定為 [/std： c + + 17](../build/reference/std-specify-language-standard-version.md)。 升級至較新的標準時引發的錯誤與使用 **寬鬆** 選項時引發的錯誤無關。

- 符合所有標準版本的程式碼，但不再被視為新式 c + + 中的最佳做法。

   若要識別建議變更的程式碼，請執行程式 [代碼分析](../code-quality/code-analysis-for-c-cpp-overview.md)。

## <a name="open-and-convert-a-legacy-project"></a>開啟和轉換舊版專案

如果您的舊版專案是以舊版 Visual Studio 為基礎，您可以在 Visual Studio 2017 或 Visual Studio 2019 中開啟它。 Visual Studio 會自動將它轉換成目前的專案架構，並支援所有最新的編譯器和 IDE 功能。

![升級專案](media/upgrade-dialog-v142.png "升級專案")

如需詳細資訊，請參閱 [Visual Studio 舊版的 c + + 專案升級](upgrading-projects-from-earlier-versions-of-visual-cpp.md)。

## <a name="search-the-code-base"></a>搜尋程式碼基底

升級程式碼基底通常牽涉到搜尋多個檔案。 若要搜尋程式碼基底中的任何程式碼，請按 **Ctrl + T** 以顯示 [ **移至所有** 搜尋] 方塊。

![移至全部](media/go-to-all.png "移至全部")

若要縮小搜尋範圍，請輸入1個字母篩選準則的其中一個，後面接著一個空格，然後是您要尋找的內容。

## <a name="error-list"></a>錯誤清單

當您將所需的 c + + 語言標準和任何其他編譯器選項都 (**專案**  >  **屬性**  >  **一般**) 之後，請按**Ctrl + Shift + B**以編譯您的專案。 您可以預期會在程式碼中的不同位置，以紅色波浪線的形式來查看一些錯誤和警告。 錯誤也會出現在 [ **錯誤清單**] 中。 如需特定錯誤的詳細資訊，請按一下錯誤碼以移至檔中的說明頁面。 以 "C" 開頭的錯誤碼是編譯器錯誤。 開頭為 "MSB" 的程式碼是 MSBuild 錯誤，表示專案設定有問題。

![錯誤清單中的編譯器和 MSBuild 錯誤](media/compiler-error-list.png "錯誤清單中的編譯器和 MSBuild 錯誤")

## <a name="document-health-indicator"></a>文件健康情況指示器

編輯器底部的檔健康狀態指標會顯示目前檔中的錯誤和警告數目，並可讓您直接從一個警告/錯誤流覽至下一個警告/錯誤。

![檔健康情況指標](media/document-health-indicator.png "檔健康情況指標")

在許多情況下，您可以在有關 Visual Studio 變更歷程記錄和一致性改善的檔中找到特定錯誤的詳細資訊。

- [C++ 一致性改善](../overview/cpp-conformance-improvements.md)
- [Visual C++ 變更歷程記錄 2003-2015](visual-cpp-change-history-2003-2015.md)
- [潛在升級問題概觀](overview-of-potential-upgrade-issues-visual-cpp.md)

## <a name="use-code-analysis-to-modernize-your-code"></a>使用程式碼分析將程式碼現代化

升級時，建議您在專案上執行程式碼分析，使程式碼符合 Microsoft 原生建議規則的最小值。 這些規則是由 Microsoft 所定義的規則與 [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)子集的組合。 藉由遵守這些規範，您將可大幅減少或消除常見的錯誤來源，同時讓您的程式碼更容易閱讀，因此更容易維護。 預設會啟用使用 Microsoft 原生建議規則進行程式碼分析。 您可以在 [**專案**  >  **屬性**程式  >  **代碼分析**] 下啟用其他規則。 違反其中一個規則的程式碼會標示為警告，並在程式碼編輯器中加上綠色波浪線。 將滑鼠停留在波浪線上以查看描述問題的 **QuickInfo** 工具提示。

![程式碼分析工具提示](media/code-analysis-tooltip.png "程式碼分析警告")

按一下 [程式 **代碼** ] 資料行中的 [篩選] 圖示，以選擇要顯示的警告。

![錯誤清單中的程式碼分析篩選](media/code-analysis-filter.png "錯誤清單中的程式碼分析篩選")

程式碼分析錯誤和警告也會出現在 **錯誤清單** 中，就像編譯器錯誤一樣。

![錯誤清單中的程式碼分析警告](media/code-analysis-error-list.png "錯誤清單中的程式碼分析警告")

您可以變更作用中的規則，並建立自訂規則集。 如需使用程式碼分析的詳細資訊，請參閱 [C/c + + 的程式碼分析總覽](../code-quality/code-analysis-for-c-cpp-overview.md)。

## <a name="use-quick-actions-to-modernize-code"></a>使用快速動作將程式碼現代化

程式碼編輯器會針對一些常見的建議提供快速動作。 當燈泡圖示出現時，您可以按一下它以查看可用的快速動作。

### <a name="convert-macros-to-constexpr-functions"></a>將宏轉換成 constexpr 函數

下圖顯示使用稱為的宏 `AVERAGE` ，其具有預設的語義顏色標示。 影像也會顯示滑鼠游標停留在其上方時所顯示的 QuickInfo 工具提示：

![QuickInfo 宏展開](media/macro-expansion-quick-info.png "QuickInfo 工具提示宏展開")

因為新式 c + + 不建議使用宏，Visual Studio 可讓您輕鬆地將宏轉換成函式 **`constexpr`** ：

1. 以滑鼠右鍵按一下 `AVERAGE` ，然後選擇 [ **移至定義**]。
2. 按一下螺絲起子圖示，然後選擇 [**將宏轉換成 constexpr** ]

   ![對 constexpr 的快速動作宏](media/quick-action-macro-to-constexpr.png "對 constexpr 的快速動作宏")

宏的轉換如下所示：

![constexpr 函數](media/constexpr-function.png "constexpr 函數")

和的呼叫 `AVERAGE` 現在會以色彩標示為函式呼叫，而快速諮詢工具提示會顯示函式的推算型別：

![constexpr 函式呼叫](media/constexpr-function-call.png "constexpr 函式呼叫")

### <a name="initialize-variables"></a>將變數初始化

未初始化的變數可以保存造成嚴重錯誤的隨機值。 程式碼分析會旗標這些實例，而編輯器會提供快速動作：

![將變數初始化](media/init-variable.png "初始化變數快速動作")

### <a name="convert-to-raw-string-literal"></a>轉換為原始字串常值

原始字串常值較不容易出錯，而且類型比具有內嵌 escape 字元的字串更方便。 以滑鼠右鍵按一下字串，然後選擇 [ **快速動作** ]，將它轉換成原始字串常值。

![原始字串常值](media/raw-string-literal.png "原始字串常值")

字串會轉換為： `R"(C:\Users\bjarnes\demo\output.txt)"` 。
