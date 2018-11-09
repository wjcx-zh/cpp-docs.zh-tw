---
title: 逐步解說：使用專案和方案 (C++)
ms.date: 09/14/2018
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 6cbd4cf86e6828d637430c468afd1306665746a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459731"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>逐步解說：使用專案和方案 (C++)

以下說明如何在 Visual Studio 中建立 C++ 專案，加入程式碼，然後建置並執行專案。 本逐步解說中的專案是追蹤有多少玩家正在進行不同的撲克牌遊戲的程式。

在 Visual Studio 中，工作是組織在專案和方案中。 方案可以具備一個以上的專案，例如 DLL 和參考該 DLL 的可執行檔。 如需詳細資訊，請參閱[方案和專案](/visualstudio/ide/solutions-and-projects-in-visual-studio)。

## <a name="before-you-start"></a>開始之前

若要完成這個逐步解說，您需要 Visual Studio 2017 15.3 版或更新版本。 如果您需要複本，以下是簡短指南：[在 Visual Studio 中安裝 C++ 支援](../build/vscpp-step-0-installation.md)。 如果尚未完成，請在安裝後透過 "Hello, World" 教學課程執行下列步驟，確定 Visual C++ 已正確安裝且運作正常。

如果您了解 C++ 語言的基本概念，並知道編譯器、連結器和偵錯工具的用途，會很有幫助。 本教學課程也會假設您已熟悉 Windows，以及如何使用功能表和對話方塊。

## <a name="create-a-project"></a>建立專案

若要建立專案，請先選擇專案類型範本。 Visual Studio 會針對每個專案類型，設定編譯器設定，並根據類型產生稍後可以修改的起始程式碼。

### <a name="to-create-a-project"></a>若要建立專案

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [已安裝的]，然後選取 [Visual C++] (如果尚未開啟)。

1. 在中間窗格的已安裝的範本清單中，選取 [Windows 主控台應用程式]。

   > [!NOTE]
   > 在舊版 Visual Studio 中，已安裝的範本稱為 **Win32 主控台應用程式**。

1. 在 [名稱] 方塊中輸入專案名稱。 在本範例中，請輸入 *Game*。

   您可以接受 [位置] 下拉式清單的預設位置，輸入其他位置，或選擇 [瀏覽] 按鈕瀏覽至您要儲存專案的目錄。

   當您建立專案時，Visual Studio 會將此專案放入方案中。 根據預設，方案的名稱與專案名稱相同， 您可以變更 [方案名稱] 方塊中的名稱，但在本範例中，請保留預設名稱。

1. 選擇 [確定] 按鈕以建立專案。

   Visual Studio 會建立您的新方案和專案檔，並開啟適用於所產生之 Game.cpp 原始程式碼檔的編輯器。

## <a name="organize-projects-and-files"></a>組織專案及檔案

您可以使用 [方案總管] 來組織並管理方案中的專案、檔案及其他資源。

這部分的逐步解說說明如何將類別新增至專案。 當您新增類別時，Visual Studio 會新增對應的 .h 和 .cpp 檔案。 您可以在 [方案總管] 中查看結果。

### <a name="to-add-a-class-to-a-project"></a>若要將類別加入至專案

1. 如果 Visual Studio 中未顯示 [方案總管] 視窗，請在功能表列上選擇 [檢視] > [方案總管]。

1. 在 [方案總管] 中選取 **Game** 專案。 在功能表列上，選擇 [專案] > [新增類別]。

1. 在 [新增類別] 對話方塊的 [類別名稱] 方塊中，輸入 *Cardgame*。 不要修改預設檔案名稱及設定。 選擇 [確定]  按鈕。

   Visual Studio 會建立新的檔案，並將其新增至您的專案。 您可以在 [方案總管] 視窗中查看這些檔案。 Cardgame.h 和 Cardgame.cpp 檔案會在編輯器中開啟。

1. 編輯 Cardgame.h 檔案，並進行下列變更：

   - 在類別定義的左邊大括號後面加入兩個私用資料成員。
      <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - 修改 Visual Studio 產生的預設建構函式。 在 `public:` 存取指定名稱之後，尋找如下所示的程式碼行：

      `Cardgame();`

      修改建構函式，使其接受一個類型為 `int`、名稱為 *players* 的參數。

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]--> `Cardgame(int players);`

   - 在預設解構函式之後，新增 `static int` 成員函式 (名為 *GetParticipants*) 的內嵌宣告，這個函式不接受參數，且會傳回 `totalParticipants` 值。

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]--> `static int GetParticipants() { return totalParticipants; }`

   在您變更之後，Cardgame.h 檔案應類似以下程式碼：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->
   ```cpp
   #pragma once
   class Cardgame
   {
       int players;
       static int totalParticipants;
   public:
       Cardgame(int players);
       ~Cardgame();
       static int GetParticipants() { return totalParticipants; }
   };
   ```

   程式行 `#pragma once` 指示編譯器只包含標頭檔一次。 如需詳細資訊，請參閱 [once](../preprocessor/once.md)。 如需上述標頭檔中其他 C++ 關鍵字的資訊，請參閱 [class](../cpp/class-cpp.md)、[int](../cpp/fundamental-types-cpp.md)、[static](../cpp/storage-classes-cpp.md) 和 [public](../cpp/public-cpp.md)。

1. 選擇編輯窗格頂端的 [Cardgame.cpp] 索引標籤以開啟檔案進行編輯。

1. 刪除檔案的所有內容並取代為下列程式碼：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->
   ```cpp
   #include "pch.h"
   #include "Cardgame.h"
   #include <iostream>

   using namespace std;

   int Cardgame::totalParticipants = 0;

   Cardgame::Cardgame(int players)
       : players(players)
   {
       totalParticipants += players;
       cout << players << " players have started a new game.  There are now "
            << totalParticipants << " players in total." << endl;
   }

   Cardgame::~Cardgame()
   {
   }
   ```

   > [!NOTE]
   > 輸入程式碼時，您可以使用自動完成。 例如，如果您使用鍵盤輸入此程式碼，您可以輸入 *pl* 或 *tot*，然後按 **Ctrl**+**空格鍵**。 自動完成功能會替您輸入 `players` 或 `totalParticipants`。

## <a name="add-test-code-to-your-main-function"></a>將測試程式碼新增至 main 函式

將一些程式碼新增至測試新函式的應用程式。

### <a name="to-add-test-code-to-the-project"></a>將測試程式碼新增至專案

1. 在 **Game.cpp** 編輯器視窗中，將現有的程式碼取代為：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->
   ```cpp
   // Game.cpp : Defines the entry point for the console application.
   //

   #include "pch.h"
   #include "Cardgame.h"
   #include <iostream>

   using namespace std;

   void PlayGames()
   {
       Cardgame bridge(4);
       Cardgame blackjack(8);
       Cardgame solitaire(1);
       Cardgame poker(5);
   }

   int main()
   {
       PlayGames();
       return 0;
   }
   ```
此程式碼會將測試函式 `PlayGames` 新增至原始程式碼，並在 `main` 中呼叫它。

## <a name="build-and-run-your-app-project"></a>建置並執行應用程式專案

接下來，建置專案並執行應用程式。

### <a name="to-build-and-run-the-project"></a>若要建置及執行專案

1. 在功能表列上選擇 [建置] > [建置解決方案]。

   建置的輸出會顯示在 [輸出] 視窗中。 如果建置成功，輸出應該看起來像這樣：

   ```Output
   1>------ Build started: Project: Game, Configuration: Debug Win32 ------
   1>pch.cpp
   1>Cardgame.cpp
   1>Game.cpp
   1>Generating Code...
   1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
   ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
   ```

   [輸出] 視窗可能顯示不同的步驟，視組建組態而定。但若專案建置成功，最後一行應該與顯示的輸出相似。

   如果建置失敗，請將您的程式碼與在前面步驟中顯示的程式碼做比較。

1. 若要執行專案，請在功能表列上選擇 [偵錯] > [啟動但不偵錯]。 此時應該會顯示主控台視窗，且輸出應該類似如下：

   ```Output
   4 players have started a new game.  There are now 4 players in total.
   8 players have started a new game.  There are now 12 players in total.
   1 players have started a new game.  There are now 13 players in total.
   5 players have started a new game.  There are now 18 players in total.
   ```
按任意鍵以關閉主控台視窗。

恭喜，您已成功建置應用程式專案和方案。 若要深入了解如何在 Visual Studio 中建置 C++ 程式碼專案，請繼續進行逐步解說。

## <a name="next-steps"></a>後續步驟

**上一個主題：**[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**下一個主題：**[逐步解說：建置專案 (C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[建置 C/C++ 程式](../build/building-c-cpp-programs.md)<br/>
