---
title: 逐步解說：偵錯專案 (C++)
ms.date: 09/14/2018
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
ms.openlocfilehash: 0a1ceddca3234ead7d10cc839d41a6d644ec1866
ms.sourcegitcommit: 9e85c2e029d06b4c1c69837437468718b4d54908
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "57812027"
---
# <a name="walkthrough-debugging-a-project-c"></a>逐步解說：偵錯專案 (C++)

在這個逐步解說中，您會修改程式以修正在測試專案時所發現的問題。

## <a name="prerequisites"></a>必要條件

- 本逐步解說假設您已了解 C++ 語言的基本概念。

- 也會假設您已完成先前列於[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中的相關逐步解說。

### <a name="to-fix-a-program-that-has-a-bug"></a>修正具有 Bug 的程式

1. 若要查看 `Cardgame` 物件被終結時發生什麼事，請檢視 `Cardgame` 類別的解構函式。

   在功能表列上選擇 [檢視] > [類別檢視]。

   在 [類別檢視] 視窗中，展開 [Game] 專案樹狀結構並選取 [Cardgame] 類別來顯示類別成員和方法。

   開啟 **~Cardgame(void)** 解構函式的捷徑功能表，然後選擇 [移至定義]。

1. 若要在 Cardgame 結束時減少 `totalParticipants`，請在 `Cardgame::~Cardgame` 解構函式的左右大括弧之間新增下列程式碼。

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]

1. 在您變更之後，Cardgame.cpp 檔案應類似以下程式碼：

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]

1. 在功能表列上選擇 [建置] > [建置解決方案]。

1. 當建置完成時，可以選擇功能表列上的 [偵錯] > [開始偵錯]，或是選擇 **F5** 鍵，以偵錯模式執行程式。 程式會在第一個中斷點上暫停。

1. 若要逐步執行程式，請在功能表列上，選擇 [偵錯] > [不進入函式]，或選擇 **F10** 鍵。

   請注意，在每個 `Cardgame` 建構函式執行後，`totalParticipants` 的值都會增加。 當 `PlayGames` 函式返回時，因為每個 `Cardgame` 執行個體會超出範圍而被刪除 (和呼叫解構函式)，所以 `totalParticipants` 會減少。 就在執行 `return` 陳述式之前，`totalParticipants` 等於 0。

1. 繼續逐步執行程式直到程式結束，或選擇功能表列上的 [偵錯] > [執行]，或是選擇 **F5** 鍵來執行程式。

## <a name="next-steps"></a>後續步驟

**上一步：**[逐步解說：測試專案 (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
**下一步：**[逐步解說：部署程式 (C++)](../ide/walkthrough-deploying-your-program-cpp.md)<br/>

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[專案和建置系統](../build/projects-and-build-systems-cpp.md)<br/>
