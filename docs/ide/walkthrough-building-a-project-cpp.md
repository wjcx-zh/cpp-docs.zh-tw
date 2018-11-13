---
title: 逐步解說：建置專案 (C++)
ms.date: 09/14/2018
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
ms.openlocfilehash: c12cd50dd92e728c88945cd83029f7e5e62816da
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524153"
---
# <a name="walkthrough-building-a-project-c"></a>逐步解說：建置專案 (C++)

在這個逐步解說中，您要刻意在程式碼中加入 Visual C++ 語法錯誤，以便了解編譯錯誤的樣貌及其修正方式。 當您編譯專案時，會有錯誤訊息指出發生了什麼問題以及發生問題的位置。

## <a name="prerequisites"></a>必要條件

- 本逐步解說假設您已了解 C++ 語言的基本概念。

- 也會假設您已完成先前列於[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中的相關逐步解說。

### <a name="to-fix-compilation-errors"></a>若要修正編譯錯誤

1. 在 TestGames.cpp 中，刪除最後一行中的分號，讓其看起來類似此陳述式：

   `return 0`

1. 在功能表列上選擇 [建置] > [建置解決方案]。

1. 在 [錯誤清單] 視窗中的訊息指出專案中有建置錯誤。 訊息描述看起來類似此錯誤訊息：

   `error C2143: syntax error: missing ';' before '}'`

   若要檢視這個錯誤的說明資訊，請在 [錯誤清單] 視窗中醒目提示該錯誤，然後選擇 **F1** 鍵。

1. 將分號加回到發生語法錯誤的那一行結尾：

   `return 0;`

1. 在功能表列上選擇 [建置] > [建置解決方案]。

   [輸出] 視窗中的訊息顯示專案已成功編譯。

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>Game.cpp
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

## <a name="next-steps"></a>後續步驟

**上一步：**[逐步解說：使用專案和方案 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)<br/>
**下一步：**[逐步解說：測試專案 (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>

## <a name="see-also"></a>請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[建置 C/C++ 程式](../build/building-c-cpp-programs.md)<br/>
