---
title: 演練:分析 C/C++缺陷代碼
description: 演示如何在 Visual Studio 中使用 Microsoft C++的代碼分析。
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: fe9b3775199b2a18cf940b99e87852350f1fbea9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370207"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>演練:分析 C/C++缺陷代碼

本演練演示如何分析 C/C++代碼的潛在代碼缺陷。 它使用 C/C++ 代碼的代碼分析工具。

在本演練中,您將:

- 對本機代碼運行代碼分析。
- 分析代碼缺陷警告。
- 將警告視為錯誤。
- 對原始碼進行一些規範,以改進程式碼缺陷分析。

## <a name="prerequisites"></a>Prerequisites

- [CppDemo 範例](../code-quality/demo-sample.md)的副本。
- 對C/C++的基本理解。

## <a name="run-code-analysis-on-native-code"></a>在本機代碼上執行代碼分析

### <a name="to-run-code-defect-analysis-on-native-code"></a>在本機代碼上執行程式碼缺陷分析

::: moniker range=">=vs-2019"

1. 在視覺工作室中打開 CppDemo 解決方案。

     CppDemo 解決方案現在填充**解決方案資源管理員**。

1. 在 **「生成」** 功能表上,選擇 **「重建解決方案**」。

     解決方案生成時沒有任何錯誤或警告。

1. 在**解決方案資源管理員中**,選擇代碼缺陷專案。

1. 在 **「專案」** 選單上,選擇 **「屬性**」。

     將顯示「**代碼缺陷屬性頁**」 對話框。

1. 選擇**代碼分析**屬性頁。

1. 將**生成屬性上的啟用代碼分析**更改為 **"是**" 選取 [確定]**** 儲存您的變更。

1. 重建代碼缺陷專案。

     代碼分析警告顯示在 **「錯誤清單」** 視窗中。

::: moniker-end

::: moniker range="<=vs-2017"

1. 在視覺工作室中打開 CppDemo 解決方案。

     CppDemo 解決方案現在填充**解決方案資源管理員**。

1. 在 **「生成」** 功能表上,選擇 **「重建解決方案**」。

     解決方案生成時沒有任何錯誤或警告。

     > [!NOTE]
     > 在 Visual Studio 2017 中`E1097 unknown attribute "no_init_all"`,您可能會在 IntelliSense 引擎中看到虛假警告。 您可以放心地忽略此警告。

1. 在**解決方案資源管理員中**,選擇代碼缺陷專案。

1. 在 **「專案」** 選單上,選擇 **「屬性**」。

     將顯示「**代碼缺陷屬性頁**」 對話框。

1. 選擇**代碼分析**屬性頁。

1. 勾選此選項 **, 在產生時啟用代碼分析**「複選框。 選取 [確定]**** 儲存您的變更。

1. 重建代碼缺陷專案。

     代碼分析警告顯示在 **「錯誤清單」** 視窗中。

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>分析代碼錯誤警告

1. 在 **「查看」** 選單上,選擇 **「錯誤清單**」。

     此功能表項可能不可見。 這取決於您在可視化工作室中選擇的開發人員配置檔。 您可能需要在 **「查看」** 選單上指向**其他 Windows,** 然後選擇 **「錯誤清單**」 。

1. 在 **「錯誤清單」** 視窗中,按兩下以下警告:

     C6230:語義上不同類型的隱式強制轉換:在布爾上下文中使用 HRESULT。

     代碼編輯器顯示在函數`bool ProcessDomain()`內引起警告的行。 此警告指示`HRESULT`正在「if」語句中使用,其中預期存在布林結果。 這通常是一個錯誤,因為當`S_OK`HRESULT 從函數傳回時,它表示成功,但當轉換為布林值時,`false`它將評估為 。

1. 使用`SUCCEEDED`宏更正此警告,宏將`true`轉換為`HRESULT`返回值指示成功時。 您的代碼應類似於以下代碼:

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. 在**錯誤清單中**,按兩下以下警告:

     C6282:不正確的運算符:在布爾上下文中分配常量。 請考慮改用"

1. 通過測試相等性來更正此警告。 您的代碼應類似於以下代碼:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. 通過初始化和`i``j`0 更正**錯誤清單中**的剩餘 C6001 警告。

1. 重建代碼缺陷專案。

     專案生成時沒有任何警告或錯誤。

## <a name="correct-source-code-annotation-warnings"></a>正確的源碼註解警告

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>在註解.c 中開啟原始碼註解警告

::: moniker range=">=vs-2019"

1. 在解決方案資源管理器中,選擇註釋專案。

1. 在 **「專案」** 選單上,選擇 **「屬性**」。

     將顯示 **「註釋屬性頁**」對話框。

1. 選擇**代碼分析**屬性頁。

1. 將**生成屬性上的啟用代碼分析**更改為 **"是**" 選取 [確定]**** 儲存您的變更。

::: moniker-end

::: moniker range="<=vs-2017"

1. 在解決方案資源管理器中,選擇註釋專案。

1. 在 **「專案」** 選單上,選擇 **「屬性**」。

     將顯示 **「註釋屬性頁**」對話框。

1. 選擇**代碼分析**屬性頁。

1. 勾選此選項 **, 在產生時啟用代碼分析**「複選框。 選取 [確定]**** 儲存您的變更。

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>解記的原始碼註解警告

1. 重建註釋專案。

1. 在 **「生成」** 選單上,選擇 **「在註釋上運行代碼分析**」。

1. 在**錯誤清單中**,按兩下以下警告:

     C6011:取消引用 NULL 指標"newNode"。

     此警告指示調用方檢查返回值失敗。 在這種情況下,調用可能會`AllocateNode`返回 NULL 值。 有關的函數聲明,請參閱 註釋.h`AllocateNode`標頭 檔。

1. 游標位於發生警告的註釋.cpp 檔中的位置。

1. 要更正此警告,請使用"if"語句來測試返回值。 您的代碼應類似於以下代碼:

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. 重建註釋專案。

     專案生成時沒有任何警告或錯誤。

## <a name="use-source-code-annotation-to-discover-more-issues"></a>使用原始碼註解發現更多問題

### <a name="to-use-source-code-annotation"></a>使用原始碼註解

1. 批次參數與函數`AddTail`傳回值以指示指標值可能為空:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. 在 [建置]**** 功能表上，選擇 [針對方案執行程式碼分析]****。

1. 在**錯誤清單中**,按兩下以下警告:

     C6011:取消引用 NULL指標"節點"

     此警告指示傳遞到函數中的節點可能為空。

1. 要更正此警告,請使用函數開頭的"if"語句來測試傳入的值。 您的代碼應類似於以下代碼:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. 在 [建置]**** 功能表上，選擇 [針對方案執行程式碼分析]****。

     項目現在生成時沒有任何警告或錯誤。

## <a name="see-also"></a>另請參閱

[演練:分析代碼缺陷的託管代碼](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[C/C++ 的程式碼分析](../code-quality/code-analysis-for-c-cpp-overview.md)
