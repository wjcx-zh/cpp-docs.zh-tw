---
title: 在 Visual Studio 中編輯及重構 C++ 程式碼
description: 使用 Visual Studio 中的 C++ 程式碼編輯器來格式化、巡覽、了解及重構程式碼。
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.topic: overview
ms.openlocfilehash: 43c4529ae0c5ac5a8c4fae2ae402ed3c6e222c37
ms.sourcegitcommit: 426e327c9f7c3a3b02300e3f924f9786d62958e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84206215"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>在 Visual Studio 中編輯及重構 C++ 程式碼

Visual Studio 提供數種工具來協助您撰寫、編輯及重構程式碼。

## <a name="intellisense"></a>IntelliSense

IntelliSense 是一種強大的程式碼完成工具，可在您鍵入時為您提供符號與程式碼片段的建議。 Visual Studio 中的 C++ IntelliSense 會即時執行，以便在您更新程式碼基底時進行分析並提供建議。 當您鍵入更多字元時，建議的結果清單就會縮小。

![C&#43;&#43; 成員下拉式清單](../ide/media/cpp-statement-completion.png)

自動省略某些符號可縮小結果範圍。 例如，從類別外部存取類別物件的成員時，您將無法看到預設的私用成員，或受保護的成員（如果您不在子類別的內容中）。 您可以使用底部的按鈕來調整篩選。

從下拉式清單中選擇符號之後，您可以使用**Tab**、 **Enter**或其中一個其他認可字元來自動完成（預設為： `{ } [ ] ( ) . , : ; + - * / % & | ^ ! = ? @ # \` ）。 若要新增或移除此清單中的字元，請在 [快速啟動]**** (Ctrl + Q) 中搜尋 "IntelliSense"，然後選擇 [文字編輯器] > [C/C++] > [進階]**** 選項。 [成員清單認可字元]**** 選項可讓您以所需的變更自訂清單。

[成員清單篩選模式]**** 選項可控制您所看到的 IntelliSense 自動完成建議種類。 根據預設，此屬性會設定為 [模糊]****。 在模糊搜尋中，如果您有一個稱為 *MyAwesomeClass* 的符號，您可以鍵入 "MAC"，並在您的自動完成建議中尋找該類別。 模糊演算法會設定臨界值下限，符號必須符合該臨界值才會顯示在清單中。 **智慧型**篩選會顯示內含子字串符合鍵入內容的所有符號。 **前置詞**篩選則會搜尋以您所鍵入內容為開頭的字串。

如需 C++ IntelliSense 的詳細資訊，請參閱 [Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense) 和[設定 C++ IntelliSense 專案](/visualstudio/ide/visual-cpp-intellisense-configuration)。

## <a name="intellicode"></a>IntelliCode

IntelliCode 是 AI 輔助的 IntelliSense。 它會將最有可能的候選項目放在完成清單頂端。 IntelliCode 建議是根據 GitHub 上數以千計的開放原始碼專案，每個都超過 100 顆星。 與您的程式碼內容結合使用時，可量身打造完成清單，以便升級常見做法。

當撰寫 C++ 時，IntelliCode 將會在使用 C++ 標準程式庫之類的熱門程式庫時提供協助。 您的程式碼內容用來先提供最有用建議。 在下列範例中，`size` 成員函式通常會與 `sort` 函式一起使用，因此它會顯示在結果清單的頂端。

![C&#43;&#43; IntelliCode](../ide/media/intellicode-cpp.png "C + + IntelliCode")

::: moniker range="vs-2019"

在 Visual Studio 2019 中，IntelliCode 是以 **C++ 桌面開發**工作負載的選擇性元件形式提供。 若要確定 IntelliCode 在 c + + 中為作用中，請移至 [**工具]**  >  [**選項**]  >  [**IntelliCode**]  >  **[一般**]，並將 [ **c + +** **Enabled**

::: moniker-end

::: moniker range="vs-2017"

在 Visual Studio 2017 中，IntelliCode 則是以 Visual Studio Marketplace 的延伸模組形式提供。

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>預測性 IntelliSense (實驗性)

[預測性 IntelliSense]**** 是一項實驗性功能，可使用內容感知來限制 IntelliSense 下拉式清單中顯示的結果數目。 此演算法會套用類型比對，以便只顯示符合預期類型的結果。 在最簡單的情況下，如果您鍵入 `int x =` 並叫用 IntelliSense 下拉式清單，則只會看到整數或傳回整數的函式。 這項功能預設為關閉，因為它仍在開發中。 它最適合搭配全域符號；還不支援成員函式。 您可以開啟這項功能，方法是在 [快速啟動]**** 中鍵入「預測」，或移至 [工具]**** > [選項]**** > [文字編輯器]**** > [C/C++]**** > [實驗性]**** > [啟用預測性 IntelliSense]****。

若要覆寫**預測性 IntelliSense**並顯示較長的清單，請按**Ctrl + J**。如果已開啟**預測性 IntelliSense** ，叫用**Ctrl + J**會移除預測性篩選。 再次按下 **Ctrl + J** 則會從相關的成員清單結果中移除存取範圍篩選。 [IntelliSense] 下拉式清單下的（[+]）按鈕會與**Ctrl + J**執行相同的工作。將滑鼠停留在按鈕上，以查看所顯示內容的工具提示資訊。

![C&#43;&#43; 預測性 IntelliSense](../ide/media/predictive-intellisense-cpp.png "預測性 IntelliSense")

上述螢幕擷取畫面顯示下拉式清單底下的數個按鈕。 這些可讓 IntelliSense 篩選取得不同類型的結果：

- 變數和常數
- 函數
- 類型
- 巨集
- 列舉
- 命名空間

只有當按鈕與您目前的 IntelliSense 工作階段相關時，才會顯示該按鈕。 您通常不會同時看到所有按鈕。

## <a name="template-intellisense"></a>範本 IntelliSense

當插入號位於範本定義中時，隨即會出現**範本列**，它可讓您提供 IntelliSense 的範例範本引數。

![C&#43;&#43; 範本 IntelliSense 顯示現有的具現化](../ide/media/template-intellisense-cpp-1.png "範本 IntelliSense 顯示現有的具現化")

按一下 **\<T>** 圖示以展開/折迭**範本**列。 按一下鉛筆圖示，或按兩下**範本列**來開啟 [編輯]**** 視窗。

![C&#43;&#43; 範本 IntelliSense](../ide/media/template-intellisense-cpp-3.png "範本 IntelliSense")

您在視窗中所進行的編輯內容會直接套用到原始程式碼，讓您能夠即時查看影響。

範本列可以根據程式碼中的具現化自動填入候選項目。 按一下 [新增所有現有具現化]****，以查看用來在整個程式碼基底中具現化範本的所有具體引數清單。

![C&#43;&#43; 範本 IntelliSense 結果清單](../ide/media/template-intellisense-cpp-2.png "範本 IntelliSense 結果清單")

編輯器底部的視窗會顯示發現每個具現化的位置，以及其引數。

![C&#43;&#43; 範本 IntelliSense 具現化對應](../ide/media/template-intellisense-cpp-4.png "範本 IntelliSense 具現化對應")

**範本列**資訊被視為使用者專屬資訊。 它會儲存在 .vs 資料夾中，而不會認可至原始檔控制。

## <a name="error-squiggles-and-quick-fixes"></a>錯誤波浪線與快速檢修

如果編輯器偵測到您的程式碼出現問題，它會在問題底下新增有顏色的波浪線。 紅色波浪線表示無法編譯的程式碼。 綠色波浪線表示可能仍然有潛在嚴重問題的其他問題類型。 您可以開啟 [錯誤清單]**** 視窗來取得問題的相關資訊。

針對某些類型的錯誤以及一般程式碼撰寫模式，編輯器會以燈泡的形式提供 [快速檢修]**** 功能，只要您將滑鼠指標停留在波浪線上方就會出現燈泡。 請按一下向下箭號來查看建議。

在下列範例中，已宣告 `vector` 但找不到任何定義，因此編輯器會包含必要的標頭檔：

![C&#43;&#43; 快速修復](../ide/media/quick-fix-for-header-cpp.png "C + + 快速修正")

編輯器也會提供快速檢修以獲取一些重構機會。 例如，如果您在標頭檔中宣告類別，Visual Studio 將會在個別的 .cpp 檔案中為其建立定義。

![C&#43;&#43; 快速修復](../ide/media/quick-fix.png "C + + 快速修正")

## <a name="change-tracking"></a>變更追蹤

每當您變更檔案時，左側會顯示一條黃色列，表示已進行未儲存的變更。 當您儲存檔案時，該列會變成綠色。 只要在編輯器中開啟文件，就會呈現綠色列和黃色列。 它們代表您上次開啟文件以來所進行的變更。

![C&#43;&#43; 變更追蹤](../ide/media/change-tracking-cpp.png "變更追蹤")

## <a name="move-code"></a>移動程式碼

您可以選取程式碼行並按住 Alt 鍵，然後按 [向上鍵/向下鍵]****，將這些程式碼行向上及向下移動。

## <a name="insert-snippets"></a>插入程式碼片段

程式碼片段是預先定義的原始碼片段。 以滑鼠右鍵按一下單點或選取的文字，可插入程式碼片段或以程式碼片段圍繞選取的文字。 下圖顯示以 for 迴圈圍繞所選陳述式的三個步驟。 最終影像中的黃色反白顯示就是您使用 tab 鍵存取的可編輯欄位。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。

![C&#43;&#43; 插入程式碼片段下拉&#45;](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

## <a name="add-class"></a>加入類別

從 [專案]**** 功能表或從 [方案總管]**** 的操作功能表新增類別：

![在 C&#43;&#43;中新增類別](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

您也可以使用 [類別精靈] 來修改或檢查現有的類別。

![C&#43;&#43; [類別精靈]](../ide/media/vs2017-class-wizard.png)

如需詳細資訊，請參閱[使用程式碼精靈新增功能 (C++)](../ide/adding-functionality-with-code-wizards-cpp.md)。

## <a name="refactoring"></a>重構

重構可以從 [快速動作] 操作功能表下取得，或是按一下編輯器中的[燈泡](/visualstudio/ide/perform-quick-actions-with-light-bulbs)。  在 [編輯] > [重構]**** 功能表中也可以找到部分項目。  這些功能包括：

- [重新命名](refactoring/rename.md)
- [解壓縮函式](refactoring/extract-function.md)
- [執行純虛擬函式](refactoring/implement-pure-virtuals.md)
- [建立宣告/定義](refactoring/create-declaration-definition.md)
- [移動函式定義](refactoring/move-definition-location.md)
- [轉換成原始字串常值](refactoring/convert-to-raw-string-literal.md)
- [變更簽章](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>使用 ClangFormat 和 EditorConfig 施行程式碼樣式

Visual Studio 2017 和更新版本隨附 [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) 的內建支援，這是一種根據 Clang/LLVM 的 C++ 熱門程式碼格式化公用程式。 請在 [快速啟動](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) 中鍵入 "ClangFormat"，將它設定為使用其中一種常見格式：

- LLVM
- Google
- Chromium
- Mozilla
- WebKit
- Visual Studio

您也可以提供您自己的 .clang-format 或 _clang-format 檔案，將自訂規則套用至相同層級以下的所有程式碼檔案。

這些檔案可透過原始檔控制輕鬆共用，因此您可以在整個開發小組中施行程式碼撰寫慣例。

![C&#43;&#43; Clang 格式](../ide/media/clang-format-cpp.png "Clang 格式")

Visual Studio 2017 和更新版本也支援以類似方式運作的 [EditorConfig](https://editorconfig.org/)。 不過，ClangFormat 有比 EditorConfig 更多的樣式選項，包括 c + + 特有的規則。 使用 **EditorConfig** 時，您可以建立 **.editorconfig** 檔案，並將它們放在程式碼基底的不同資料夾中，用來指定這些資料夾及其子資料夾的程式碼樣式。 **.editorconfig** 檔案會取代父資料夾中的任何其他 **.editorconfig** 檔案，並覆寫任何透過 [工具]**** > [選項]**** 設定的格式設定。 您可以針對定位點與空格、縮排大小及其他項目設定一些規則。 如需詳細資訊，請參閱[使用 EditorConfig 建立可攜式自訂編輯器設定](/visualstudio/ide/create-portable-custom-editor-options)。

## <a name="other-formatting-options"></a>其他格式化選項

[快速啟動]**** 搜尋方塊提供尋找設定或工具的最快方式。 它位於主功能表上。 只要開始鍵入，自動完成清單就會篩選結果。

![Visual Studio 快速啟動](../ide/media/vs2015_cpp_quick_launch.png "快速啟動")

若要設定格式化選項，例如縮排、以大括弧完成和顏色標示，請在 [快速啟動]**** 視窗中鍵入 "C++ Formatting"。

![C++ 格式化選項](media/cpp-formatting-options.png)

您可以在**Edit**  >  主功能表的 [編輯] [**高級**] 下找到其他格式化選項。

![C++ 進階編輯選項](media/edit-advanced-cpp.png)

啟用和設定 c + + 特定編輯功能的選項位於 [**工具**] [選項] [  >  **Options**  >  **文字編輯器**] [  >  **C/c + +**] 底下。 選擇您想要設定的選項之後，您可以在對話方塊成為焦點時按下 **F1** 來取得更多說明。 針對一般程式碼格式化選項，請在 [快速啟動]**** 中鍵入 `Editor C++`。

![Visual Studio Tools > 選項](../ide/media/tools-options.png "編輯器選項")

您可以在[文字編輯器 C++ 實驗](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental)對話方塊中找到不一定包含在 Visual Studio 未來版本中的實驗性功能。 在 Visual Studio 2017 和更新版本中，您可以啟用這個對話方塊中的 [預測性 IntelliSense]****。

## <a name="see-also"></a>另請參閱

[閱讀及了解 C++ 程式碼](read-and-understand-code-cpp.md)</br>
[在 Visual Studio 中巡覽 C++ 程式碼基底](navigate-code-cpp.md)</br>
[使用 Live Share for C++ 進行共同作業](live-share-cpp.md)
