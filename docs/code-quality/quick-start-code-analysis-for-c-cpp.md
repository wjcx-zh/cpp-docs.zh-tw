---
title: 快速入門：C/C++ 的程式碼分析
description: 對 Visual Studio 中的C++代碼進行靜態分析,以檢測常見的編碼問題和缺陷。
ms.date: 04/08/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis, C/C++
ms.openlocfilehash: 43866564915ac84d227ccbf347280efe59e33351
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370578"
---
# <a name="quickstart-code-analysis-for-cc"></a>快速入門：C/C++ 的程式碼分析

您可以在 C 或 C++ 程式碼上定期執行程式碼分析，以改善您的應用程式品質。 代碼分析可以説明您找到常見問題和違反良好程式設計實踐的行為。 而且,它發現了難以通過測試發現的缺陷。 其警告與編譯器錯誤和警告不同:它搜索已知會導致問題的特定代碼模式。 也就是說,代碼是有效的,但仍可能為您或使用代碼的其他用戶創建問題。

## <a name="configure-rule-sets-for-a-project"></a>設定專案的規則集

1. 在**解決方案資源管理員**中,開啟專案名稱的快捷方式選單,然後選擇**屬性**。

1. 在「**設定**和**平臺**」清單中,可以選擇生成配置和目標平臺。

1. 要在每次使用所選配置生成專案時運行代碼分析,請選擇 **「在生成時啟用代碼分析**」複選框。 您還可以透過開啟 **「分析」** 選單,然後選擇 *「專案名稱***」 執行程式碼分析「****或 」 的程式執行程式碼分析「來手動執行程式碼分析**。

1. 選擇要使用[的規則集](using-rule-sets-to-specify-the-cpp-rules-to-run.md)或建立[自訂規則集](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor)。 如果使用 LLVM/clang-cl,請參閱[在可視化工作室中使用 Clang-Tidy](../code-quality/clang-tidy.md)來配置 Clang-Tidy 分析選項。

### <a name="standard-cc-rule-sets"></a>標準 C/C++規則集

Visual Studio 包括以下本機代碼的標準規則集:

| 規則集 | 描述 |
|--|--|
| **C++核心檢查算數規則** | 這些規則強制[從C++核心準則中執行與算術運算](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements)相關的檢查。 |
| **C++核心檢查邊界規則** | 這些規則強制執行[C++核心準則的邊界設定檔](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)。 |
| **C++核心檢查類別規則** | 這些規則強制[檢查與C++核心準則中的類](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-classes-and-class-hierarchies)有關。 |
| **C++核心檢查併發規則** | 這些規則強制[從C++核心準則中進行與併發](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cpcon-concurrency)相關的檢查。 |
| **C++核心檢查規則** | 這些規則[從C++核心準則中強制實施與相關](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)檢查相關的檢查。 |
| **C++核心檢查宣告規則** | 這些規則強制檢查與[C++核心準則的聲明](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i-interfaces)相關的檢查。 |
| **C++核心檢查列舉規則** | 這些規則[強制從C++核心準則進行與枚舉相關的檢查](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum)。 |
| **C++核心檢查實驗規則** | 這些規則收集一些實驗性檢查。 最終,我們期望這些檢查被移動到其他規則集或完全刪除。 |
| **C++核心檢查功能規則** | 這些規則強制檢查與[C++核心準則的功能相關的檢查](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f-functions)。 |
| **C++核心檢查 GSL 規則** | 這些規則強制[從C++核心準則中執行與準則支援庫](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl)相關的檢查。 |
| **C++核心檢查存留期規則** | 這些規則強制執行[C++核心準則的終身設定檔](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile)。 |
| **C++核心檢查擁有者指標規則** | 這些規則[強制從C++核心準則中執行與擁有者&lt;&gt;T](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)相關的資源管理檢查。 |
| **C++核心檢查原始指標規則** | 這些規則強制實施與[C++核心準則中的原始指標](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)相關的資源管理檢查。 |
| **C++核心檢查規則** | 這些規則強制從[C++核心準則](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines)的支票的子集。 使用此規則集可以包括除枚舉和實驗規則集之外的所有C++核心檢查規則。 |
| **C++核心檢查共用指標規則** | 這些規則強制實施與[具有C++核心準則的共用指標語義的類型](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)相關的資源管理檢查。 |
| **C++核心檢查 STL 規則** | 這些規則強制[從C++核心準則中執行與C++標準範本庫 (STL)](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib)相關的檢查。 |
| **C++核心檢查樣式規則** | 這些規則強制檢查與使用[C++核心準則的運算式和語句](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements)有關。 |
| **C++核心檢查類型規則** | 這些規則強制執行[C++核心準則的類型設定檔](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)。 |
| **C++核心檢查唯一指標規則** | 這些規則強制實施與具有[C++核心準則中唯一指標語義](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)的類型相關的資源管理檢查。 |
| **併發檢查規則** | 這些規則在C++中強制實施一組 Win32 併發模式檢查。 |
| **併發規則** | 將C++核心準則的併發規則加入到**併發檢查規則**。 |
| **微軟本機最小規則** | 這些規則側重於本機代碼中最關鍵的問題,包括潛在的安全漏洞和應用程序崩潰。 我們建議您在為本機項目創建的任何自定義規則集中包括此規則集。 |
| **Microsoft 原生建議規則** | 這些規則側重於本機代碼中最關鍵和最常見的問題。 這些問題包括潛在的安全漏洞和應用程式崩潰。 我們建議您在為本機項目創建的任何自定義規則集中包括此規則集。 此規則集旨在與 Visual Studio 專業版和更高版本配合使用。 它包括**微軟原生最小規則中的所有規則**。 |

Visual Studio 包括以下管理程式碼的標準規則集:

| 規則集 | 描述 |
|--|--|
| **微軟基本正確性規則** | 這些規則側重於邏輯錯誤和在使用框架 API 時的常見錯誤。 包括此規則集,以展開由最低推薦規則報告的警告清單中。 |
| **微軟基本設計指南規則** | 這些規則側重於強制實施最佳實踐,以使代碼易於理解和使用。 如果專案包含庫代碼,或者想要強制實施易於維護的代碼的最佳做法,請包括此規則集。 |
| **微軟延伸正確性規則** | 這些規則擴展了基本正確性規則,以最大化報告的邏輯和框架使用錯誤。 特別強調特定方案,如 COM 互通和行動應用程式。 如果這些方案之一適用於專案或發現專案中的其他問題,請考慮包括此規則集。 |
| **微軟延伸設計指南規則** | 這些規則擴展了基本設計準則規則,以最大化報告的可用性和可維護性問題。 特別強調命名準則。 如果專案包含庫代碼,或者想要強制實施編寫可維護代碼的最高標準,請考慮包括此規則集。 |
| **微軟全球化規則** | 這些規則側重於在不同語言、區域設置和區域性中使用時阻止應用程式中的數據正確顯示的問題。 如果應用程式是當地語系化和/或全球化的,請包括此規則集。 |
| **Microst 最小規則** | 這些規則側重於代碼分析最準確的代碼中最關鍵的問題。  這些規則的數量很少,它們只打算在有限的 Visual Studio 版本中運行。  將最低推薦規則.規則集與其他視覺工作室版本一起使用。 |
| **微軟託管推薦規則** | 這些規則側重於代碼中最關鍵的問題。 這些問題包括潛在的安全漏洞、應用程式崩潰以及其他重要的邏輯和設計錯誤。 我們建議您在為項目創建的任何自定義規則集中包括此規則集。 |
| **微軟混合 (C++ /CLR) 最小規則** | 這些規則側重於支援通用語言運行時C++專案中最關鍵的問題。 這些問題包括潛在的安全漏洞、應用程式崩潰以及其他重要的邏輯和設計錯誤。 我們建議您在為支援通用語言運行時C++項目創建的任何自定義規則集中包括此規則集。 |
| **微軟混合 (C++ /CLR) 推薦規則** | 這些規則側重於支援通用語言運行時C++專案中最常見的和最關鍵的問題。 這些問題包括潛在的安全漏洞、應用程式崩潰以及其他重要的邏輯和設計錯誤。 此規則集設計用於視覺工作室專業版和更高版本。 |
| **微軟安全規則** | 此規則集包含所有 Microsoft 安全規則。 包括此規則集,以最大化報告的潛在安全問題的數量。 |

要包含每個規則:

| 規則集 | 描述 |
|--|--|
| **微軟所有規則** | 此規則集包含所有規則。 運行此規則集可能會導致報告大量警告。 使用此規則集可以全面瞭解代碼中的所有問題。 它可以説明您確定哪些更集中的規則集最適合為專案運行。 |

## <a name="run-code-analysis"></a>執行程式碼分析

在「項目屬性」對話框的代碼**分析**頁上,可以配置代碼分析,以便每次生成專案時都運行。 您也可以手動執行程式碼分析。

若要針對方案執行程式碼分析：

- 在 **「產生」** 選單中,選擇**在解決方案上執行程式碼分析**。

若要針對專案執行程式碼分析：

1. 在解決方案資源管理器中,選擇專案的名稱。

1. 在 **「生成」** 選單中,在*專案名稱***上選擇「運行代碼分析**」。

在檔案上執行代碼分析,請進行:

1. 在解決方案資源管理員中,選擇檔的名稱。

1. 在 **「產生」** 選單中,選擇**在「檔案上執行程式碼分析**」,或按**Ctrl_Shift_Alt_F7**。

   編譯專案或方案並執行程式碼分析。 結果將顯示在「錯誤清單」 視窗中。

## <a name="analyze-and-resolve-code-analysis-warnings"></a>分析和解決程式碼分析警告

「錯誤清單」視窗列出了找到的代碼分析警告。 結果將顯示在表中。 如果有關特定警告的詳細資訊可用,則第一列包含擴展控制項。 選擇它可展開顯示,瞭解有關此問題的其他資訊。 如果可能的話，程式碼分析會顯示導致警告的行號和分析邏輯。

有關警告的詳細資訊(包括問題可能的解決方案),請選擇"代碼"列中的警告ID 以顯示其相應的連線説明文章。

按兩下警告以將游標移動到導致 Visual Studio 代碼編輯器中出現警告的代碼行。 或者,按"輸入所選警告」。。

在您了解問題之後，就可以在程式碼中解決問題。 然後,重新運行代碼分析,以確保警告不再顯示在錯誤清單中。

## <a name="create-work-items-for-code-analysis-warnings"></a>為代碼分析警告建立工作項目

若要記錄來自 Visual Studio 的錯誤，您可以使用工作項目追蹤功能。 要使用此功能,必須連接到 Azure DevOps 伺服器(以前是團隊基礎伺服器)的實例。

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>建立一或多個 C/C++ 程式碼警告的工作項目

1. 在錯誤清單中,展開並選擇警告

1. 在警告的快捷選單上,選擇 **「創建工作項**」,然後選擇工作項類型。

1. Visual Studio 會建立選定警告的單一工作項目，並在 IDE 的文件視窗中顯示工作項目。

1. 添加任何其他資訊,然後選擇 **"保存工作項**"。

## <a name="search-and-filter-code-analysis-results"></a>搜尋並篩選碼分析結果

您可以在多專案方案中搜尋警告訊息的詳細清單，以及篩選警告。

- **要按標題或警告 ID 篩選警告**:請在「搜尋錯誤列表」框中輸入關鍵字。

- **要按嚴重性篩選警告**:默認情況下,代碼分析消息將分配**警告**的嚴重性。 您可以將一個或多個消息的嚴重性指定為自訂規則集中**的"錯誤**"。 在 **「錯誤清單****」** 的嚴重性列上,選擇下拉箭頭,然後選擇篩選器圖示。 選擇 **「警告**」或 **「錯誤**」,僅顯示分配相應嚴重性的消息。 **選擇"全部"** 以顯示所有郵件。

## <a name="see-also"></a>另請參閱

- [C/C++ 的程式碼分析](../code-quality/code-analysis-for-c-cpp-overview.md)
