---
title: 使用 C++ Core Guidelines 檢查工具
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- CPP
ms.openlocfilehash: 9c36c17e819e954d66833f059fe794ac14898e75
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227721"
---
# <a name="use-the-c-core-guidelines-checkers"></a>使用 C++ Core Guidelines 檢查工具

C++ Core Guidelines 是一組可攜的指導方針、規則和最佳作法，用於 c + + 專家和設計人員所建立的程式碼。 Visual Studio 目前支援這些規則的子集，做為它的程式碼分析工具（c + +）的一部分。 核心指導方針檢查器預設會安裝在 Visual Studio 2017 和 Visual Studio 2019 中，並[以 NuGet 套件的形式提供 Visual Studio 2015](#vs2015_corecheck)。

## <a name="the-c-core-guidelines-project"></a>C++ Core Guidelines 專案

C++ Core Guidelines 是由 Bjarne Stroustrup 和其他人所建立，它是安全且有效率地使用新式 c + + 的指南。 這些指導方針強調靜態型別安全和資源安全性。 它們會找出用來消除或減少語言中最容易出錯之部分的方法，並建議如何讓您的程式碼更簡單，並以可靠的方式提供更佳的效能。 這些指導方針是由 Standard c + + Foundation 維護。 若要深入瞭解，請參閱檔、 [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)，並存取[GitHub](https://github.com/isocpp/CppCoreGuidelines)上的 C++ Core Guidelines 檔專案檔案。

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>啟用程式碼分析中的 C++ Core Check 方針

您可以在專案的 [**屬性頁**] 對話方塊的 [程式**代碼分析**] 區段中，選取 [**在組建上啟用程式碼分析**] 核取方塊，以啟用專案的程式碼分析。

![程式碼分析一般設定的屬性頁](media/cppcorecheck_codeanalysis_general.png)

在啟用程式碼分析時，預設會執行的 Microsoft 原生建議規則集包含 C++ Core Check 規則的子集。 若要啟用其他核心檢查規則，請按一下下拉式清單，然後選擇您想要包含的規則集：

![其他 C++ Core Check 規則集的下拉式清單](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>範例

以下是 C++ Core Check 規則可以找到的一些問題範例：

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

這個範例會示範 C++ Core Check 規則可以找到的幾個警告：

- C26494 是規則類型。5：一律初始化物件。

- C26485 是規則界限。3：沒有陣列到指標的衰減。

- C26481 是規則界限。1：不要使用指標算術。 請改用 `span`。

當您編譯此程式碼時，如果已安裝並啟用 C++ Core Check 程式碼分析規則集，則前兩個警告為輸出，但第三個是隱藏的。 以下是範例程式碼的組建輸出：

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

其中的 C++ Core Guidelines 可協助您撰寫更好且更安全的程式碼。 不過，如果您有不應套用規則或設定檔的實例，則可以直接在程式碼中將它隱藏。 您可以使用 `gsl::suppress` 屬性，讓 C++ Core Check 無法偵測和報告在下列程式碼區塊中的任何規則違規。 您可以標記個別語句，以隱藏特定規則。 您甚至可以藉由撰寫 `[[gsl::suppress(bounds)]]` 而不包含特定的規則編號來隱藏整個界限設定檔。

## <a name="supported-rule-sets"></a>支援的規則集

當 C++ Core Guidelines 檢查程式中加入新規則時，針對預先存在的程式碼所產生的警告數目可能會增加。 您可以使用預先定義的規則集來篩選要啟用哪些類型的規則。
大部分規則的參考主題都在[Visual Studio C++ Core Check 參考](code-analysis-for-cpp-corecheck.md)之下。

從 Visual Studio 2017 15.3 版，支援的規則集包括：

- **擁有者指標規則**會強制執行與[ \<T> C++ Core Guidelines 擁有者相關的資源管理檢查](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)。

- **Const 規則**會[從 C++ Core Guidelines 強制執行 Const 相關檢查](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)。

- **原始指標規則**會強制執行與[C++ Core Guidelines 的原始指標相關的資源管理檢查](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)。

- **唯一的指標規則**會強制執行與[C++ Core Guidelines 中唯一指標語義類型相關的資源管理檢查](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)。

- **界限規則**會強制執行[C++ Core Guidelines 的界限設定檔](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)。

- **類型規則**會強制執行[C++ Core Guidelines 的類型設定檔](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)。

**Visual Studio 2017 版本 15.5**：

- **類別規則**一些規則，著重于特殊成員函式和虛擬規格的正確使用。 這是建議用於[類別和類別](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class)階層的檢查子集。
- **並行處理規則**會攔截不正確宣告之 guard 物件的單一規則。 如需詳細資訊，請參閱[與並行相關的指導方針](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency)。
- 宣告**規則**[介面指導方針](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces)中的幾個規則，著重于如何宣告全域變數。
- **函數規則**可協助採用規範的兩項檢查 **`noexcept`** 。 這是[清除函數設計和實](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions)作為方針的一部分。
- **共用指標規則**在[資源管理](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource)指導方針強制執行的過程中，我們新增了幾個特定的規則，說明如何將共用指標傳遞至函式，或在本機使用。
- **樣式規則**一個簡單但重要的檢查，它 ban 了[goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto)的用法。 這是在 c + + 中改善編碼樣式和使用運算式和語句的第一個步驟。

**Visual Studio 2017 15.6 版**：

- **算術規則**用來偵測算術[溢](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow)位、不[帶正負號的作業](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned)和[位操作](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative)的規則。

您可以選擇將警告限制為只有一個或幾個群組。 除了其他 PREfast 檢查之外，**原生的最低**和**原生建議**規則集包括 C++ Core Check 規則。 若要查看可用的規則集，請開啟 [專案屬性] 對話方塊，選取 [程式**代碼 Analysis\General**]，開啟 [**規則集**] 下拉式方塊中的下拉式清單，然後挑選 **[選擇多個規則集**]。 如需在 Visual Studio 中使用規則集的詳細資訊，請參閱[使用規則集指定要執行的 c + + 規則](using-rule-sets-to-specify-the-cpp-rules-to-run.md)。

## <a name="macros"></a>巨集

C++ Core Guidelines 檢查程式隨附一個標頭檔，它會定義宏，讓您更輕鬆地在程式碼中隱藏整個類別的警告：

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

這些宏會對應到規則集，並展開為以空格分隔的警告編號清單。 藉由使用適當的 pragma 結構，您可以設定一組對專案或程式碼區段感興趣的有效規則。 在下列範例中，程式碼分析只會警告遺漏的常數修飾詞：

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>屬性

Microsoft c + + 編譯器對 GSL 隱藏屬性的支援有限。 它可以用來隱藏函式內運算式和區塊語句的警告。

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>使用命令列選項隱藏分析

除了 #pragmas 以外，您還可以在檔案的屬性頁中使用命令列選項，以隱藏專案或單一檔案的警告。 例如，若要停用檔案的警告 C26400：

1. 以滑鼠右鍵按一下中的檔案**方案總管**

1. 選擇**屬性 |C/C + + |命令列**

1. 在 [**其他選項**] 視窗中，新增 `/wd26400` 。

您可以使用命令列選項，藉由指定來暫時停用檔案的所有程式碼分析 `/analyze-` 。 這會產生警告*D9025 以 '/analyze-' 覆寫 '/analyze '*，這會提醒您稍後重新啟用程式碼分析。

## <a name="enable-the-c-core-guidelines-checker-on-specific-project-files"></a><a name="corecheck_per_file"></a>在特定專案檔案上啟用 C++ Core Guidelines 檢查程式

有時候，進行焦點程式碼分析並繼續使用 Visual Studio IDE 可能會很有用。 下列範例案例可用於大型專案，以節省組建時間並讓篩選結果變得更容易：

1. 在命令 shell 中，設定 `esp.extension` 和 `esp.annotationbuildlevel` 環境變數。
1. 若要繼承這些變數，請從命令 shell 開啟 Visual Studio。
1. 載入您的專案，並開啟其屬性。
1. 啟用 [程式碼分析]，挑選適當的規則集，但不要啟用 [程式碼分析延伸模組]。
1. 移至您要使用 C++ Core Guidelines 檢查程式分析的檔案，並開啟其屬性。
1. 選擇**C/c + + \Command 行選項**並新增`/analyze:plugin EspXEngine.dll`
1. 停用先行編譯標頭檔的使用（**c/c + + \Precompiled 標頭**）。 這是必要的，因為擴充功能引擎可能會嘗試從先行編譯標頭檔（PCH）讀取其內部資訊;如果使用預設專案選項編譯 PCH，則會不相容。
1. 請重建專案。 一般的 PREFast 檢查應該在所有檔案上執行。 由於預設不會啟用 C++ Core Guidelines 檢查程式，因此應該只在設定為使用它的檔案上執行。

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>如何使用 Visual Studio 以外的 C++ Core Guidelines 檢查程式

您可以在自動化組建中使用 C++ Core Guidelines 檢查。

### <a name="msbuild"></a>MSBuild

機器碼分析檢查程式（PREfast）會透過自訂目標檔案整合到 MSBuild 環境中。 您可以使用專案屬性加以啟用，並加入 C++ Core Guidelines 檢查程式（以 PREfast 為基礎）：

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

在匯入 Microsoft .Cpp 檔案之前，請確定您已新增這些屬性。 您可以挑選特定的規則集，或建立自訂規則集，或使用包含其他 PREfast 檢查的預設規則集。

您只能使用稍[早所述](#corecheck_per_file)的相同方法，在指定的檔案上執行 c + + Core 檢查程式，但使用 MSBuild 檔案。 您可以使用專案來設定環境變數 `BuildMacro` ：

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

如果您不想要修改專案檔，您可以在命令列上傳遞屬性：

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>非 MSBuild 專案

如果您使用不依賴 MSBuild 的組建系統，仍然可以執行檢查程式，但您必須熟悉程式碼分析引擎設定的一些內部程式。 未來不保證會支援這些內部版本。

您必須設定幾個環境變數，並為編譯器使用適當的命令列選項。 最好是在「原生工具命令提示字元」環境下工作，這樣您就不需要搜尋編譯器的特定路徑、包含目錄等等。

- **環境變數**
  - `set esp.extensions=cppcorecheck.dll`這會告訴引擎載入 C++ Core Guidelines 模組。
  - `set esp.annotationbuildlevel=ignore`這會停用處理 SAL 注釋的邏輯。 注釋不會影響 C++ Core Guidelines 檢查程式中的程式碼分析，但是它們的處理需要時間（有時候是很長的時間）。 這是選擇性設定，但強烈建議使用。
  - `set caexcludepath=%include%`我們強烈建議您停用在標準標頭上引發的警告。 您可以在這裡新增更多路徑，例如專案中通用標頭的路徑。

- **命令列選項**
  - `/analyze`啟用程式碼分析（也請考慮使用/analyze： only 和/analyze： quiet）。
  - `/analyze:plugin EspXEngine.dll`此選項會將程式碼分析延伸模組引擎載入至 PREfast。 此引擎接著會載入 C++ Core Guidelines 檢查程式。

## <a name="use-the-guideline-support-library"></a>使用指導方針支援程式庫

指導方針支援程式庫的設計可協助您遵循核心指導方針。 GSL 包含的定義可讓您以更安全的替代專案來取代容易出錯的結構。 例如，您可以將一 `T*, length` 對參數取代為 `span<T>` 類型。 GSL 可于取得 [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) 。 此程式庫是開放原始碼，因此您可以查看來源、進行批註或參與。 您可以在找到此專案 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) 。

## <a name="use-the-c-core-check-guidelines-in-visual-studio-2015-projects"></a><a name="vs2015_corecheck"></a>使用 Visual Studio 2015 專案中的 C++ Core Check 方針

如果您使用 Visual Studio 2015，預設不會安裝 C++ Core Check 程式碼分析規則集。 您必須先執行一些額外的步驟，才能啟用 Visual Studio 2015 中的 C++ Core Check 程式碼分析工具。 Microsoft 使用 Nuget 套件提供 Visual Studio 2015 專案的支援。 此套件的名稱為 CppCoreCheck，可從取得 [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) 。 此套件要求您至少安裝了 Visual Studio 2015 Update 1。

此套件也會安裝另一個套件做為相依性，也就是僅限標頭的指導方針支援程式庫（GSL）。 您也可以在 GitHub 上取得 GSL，網址為 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) 。

由於載入程式碼分析規則的方式，您必須將 CppCoreCheck NuGet 套件安裝到您想要在 Visual Studio 2015 內檢查的每個 c + + 專案中。

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>若要在 Visual Studio 2015 中將 CppCoreCheck 套件新增至您的專案

1. 在**方案總管**中，以滑鼠右鍵按一下您要新增封裝之方案中的專案內容功能表。 選擇 [**管理 Nuget 套件**] 以開啟 [ **nuget 套件管理員**]。

1. 在 [ **NuGet 套件管理員**] 視窗中，搜尋 CppCoreCheck。

    ![[Nuget 套件管理員] 視窗會顯示 CppCoreCheck 套件](../code-quality/media/cppcorecheck_nuget_window.png)

1. 選取 [CppCoreCheck] 套件，然後選擇 [**安裝**] 按鈕，將規則新增至您的專案。

   NuGet 套件會將額外的 MSBuild *.targets*檔案新增至您的專案，當您在專案上啟用程式碼分析時，就會叫用這個檔案。 這個 *.targets*檔案會將 C++ Core Check 規則新增為 Visual Studio 程式碼分析工具的額外延伸模組。 安裝封裝之後，您可以使用 [屬性頁] 對話方塊來啟用或停用已釋放和實驗性規則。

## <a name="see-also"></a>另請參閱

- [Visual Studio C++ Core Check 參考](code-analysis-for-cpp-corecheck.md)
