---
title: 逐步解說：分析 C/c + + 程式碼是否有瑕疵
description: 示範如何在 Visual Studio 中搭配使用程式碼分析與 Microsoft c + +。
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: 65da18f5f6d1972276f1cb8e306e82314282e40a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227708"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>逐步解說：分析 C/c + + 程式碼是否有瑕疵

本逐步解說示範如何分析 C/c + + 程式碼是否有潛在的程式碼缺失。 它會使用 C/c + + 程式碼的程式碼分析工具。

在本逐步解說中，您將會：

- 針對機器碼執行程式碼分析。
- 分析程式碼瑕疵警告。
- 將警告視為錯誤。
- 標注原始程式碼以改善程式碼缺失分析。

## <a name="prerequisites"></a>必要條件

- [CppDemo 範例](../code-quality/demo-sample.md)的複本。
- C/c + + 的基本瞭解。

## <a name="run-code-analysis-on-native-code"></a>針對機器碼執行程式碼分析

### <a name="to-run-code-defect-analysis-on-native-code"></a>若要在機器碼上執行程式碼瑕疵分析

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中開啟 CppDemo 方案。

     CppDemo 解決方案現在會填入**方案總管**。

1. 在 [**建立**] 功能表上，選擇 [**重建方案**]。

     此解決方案會建立，且不會出現任何錯誤或警告。

1. 在 [**方案總管**中，選取 [CodeDefects] 專案。

1. 在 [**專案**] 功能表上，選擇 [**屬性**]。

     [ **CodeDefects 屬性頁**] 對話方塊隨即顯示。

1. 選取 [程式**代碼分析**] 屬性頁。

1. 將 [**啟用組建的程式碼分析**] 屬性變更為 **[是]**。 選取 [確定]**** 儲存您的變更。

1. 重建 CodeDefects 專案。

     程式碼分析警告會顯示在 [**錯誤清單**] 視窗中。

::: moniker-end

::: moniker range="<=vs-2017"

1. 在 Visual Studio 中開啟 CppDemo 方案。

     CppDemo 解決方案現在會填入**方案總管**。

1. 在 [**建立**] 功能表上，選擇 [**重建方案**]。

     此解決方案會建立，且不會出現任何錯誤或警告。

     > [!NOTE]
     > 在 Visual Studio 2017 中，您可能會 `E1097 unknown attribute "no_init_all"` 在 IntelliSense 引擎中看到假的警告。 您可以放心地忽略此警告。

1. 在 [**方案總管**中，選取 [CodeDefects] 專案。

1. 在 [**專案**] 功能表上，選擇 [**屬性**]。

     [ **CodeDefects 屬性頁**] 對話方塊隨即顯示。

1. 選取 [程式**代碼分析**] 屬性頁。

1. 選取 [**在組建上啟用程式碼分析**] 核取方塊。 選取 [確定]**** 儲存您的變更。

1. 重建 CodeDefects 專案。

     程式碼分析警告會顯示在 [**錯誤清單**] 視窗中。

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>若要分析程式碼瑕疵警告

1. 在 [ **View** ] 功能表上，選擇 [**錯誤清單**]。

     這個功能表項目可能不會顯示。 這取決於您在 Visual Studio 中選擇的開發人員設定檔。 您可能必須指向 [ **View** ] 功能表上的 [**其他視窗**]，然後選擇 [**錯誤清單**]。

1. 在 [**錯誤清單**] 視窗中，按兩下下列警告：

     C6230：語義不同類型之間的隱含轉換：在布林內容中使用 HRESULT。

     [程式碼編輯器] 會顯示在函式內造成警告的行 `bool ProcessDomain()` 。 此警告表示 `HRESULT` 在預期布林結果的 ' if ' 語句中使用了。 這通常是錯誤的，因為當 HRESULT 從函式傳回時， `S_OK` 它會指出成功，但轉換成布林值時，它會評估為 **`false`** 。

1. 請使用宏來更正這個警告 `SUCCEEDED` ， **`true`** 當傳回 `HRESULT` 值表示成功時，它會轉換為。 您的程式碼應該類似下列程式碼：

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. 在 [**錯誤清單**中，按兩下下列警告：

     C6282：不正確的運算子：在布林內容中指派常數。 請考慮改為使用 ' = = '。

1. 藉由測試是否相等來更正此警告。 您的程式碼看起來應該與下列程式碼類似：

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. 藉由**Error List** `i` 將和初始化為0，修正錯誤清單中的其餘 C6001 警告 `j` 。

1. 重建 CodeDefects 專案。

     專案建立時不會出現任何警告或錯誤。

## <a name="correct-source-code-annotation-warnings"></a>正確的原始程式碼批註警告

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>若要啟用注釋 c 中的原始程式碼批註警告

::: moniker range=">=vs-2019"

1. 在 [方案總管中，選取 [注釋] 專案。

1. 在 [**專案**] 功能表上，選擇 [**屬性**]。

     [**批註屬性頁**] 對話方塊隨即顯示。

1. 選取 [程式**代碼分析**] 屬性頁。

1. 將 [**啟用組建的程式碼分析**] 屬性變更為 **[是]**。 選取 [確定]**** 儲存您的變更。

::: moniker-end

::: moniker range="<=vs-2017"

1. 在 [方案總管中，選取 [注釋] 專案。

1. 在 [**專案**] 功能表上，選擇 [**屬性**]。

     [**批註屬性頁**] 對話方塊隨即顯示。

1. 選取 [程式**代碼分析**] 屬性頁。

1. 選取 [**在組建上啟用程式碼分析**] 核取方塊。 選取 [確定]**** 儲存您的變更。

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>更正 annotation 中的原始程式碼批註警告

1. 重建注釋專案。

1. 在 [**建立**] 功能表上，選擇 [**在批註上執行程式碼分析**]。

1. 在 [**錯誤清單**中，按兩下下列警告：

     C6011：引用 Null 指標 ' newNode '。

     此警告表示呼叫端無法檢查傳回值。 在此情況下，對的呼叫 `AllocateNode` 可能會傳回 Null 值。 請參閱的函式宣告的注釋 .h 標頭檔 `AllocateNode` 。

1. 游標位於出現警告之注釋 .cpp 檔案中的位置。

1. 若要修正這個警告，請使用 ' if ' 語句來測試傳回值。 您的程式碼應該類似下列程式碼：

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. 重建注釋專案。

     專案建立時不會出現任何警告或錯誤。

## <a name="use-source-code-annotation-to-discover-more-issues"></a>使用原始程式碼注釋探索更多問題

### <a name="to-use-source-code-annotation"></a>若要使用原始程式碼注釋

1. 標注函式的型式參數和傳回值， `AddTail` 以指出指標值可能為 null：

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. 在 [建置]**** 功能表上，選擇 [針對方案執行程式碼分析]****。

1. 在 [**錯誤清單**中，按兩下下列警告：

     C6011：引用 Null 指標 ' node '。

     此警告表示傳入函數的節點可能是 null。

1. 若要修正這個警告，請使用函式開頭的 ' if ' 語句來測試傳入的值。 您的程式碼應該類似下列程式碼：

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. 在 [建置]**** 功能表上，選擇 [針對方案執行程式碼分析]****。

     專案現在會建立，而不會出現任何警告或錯誤。

## <a name="see-also"></a>另請參閱

[逐步解說：分析受控碼的程式碼缺失](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[C/C++ 的程式碼分析](../code-quality/code-analysis-for-c-cpp-overview.md)
