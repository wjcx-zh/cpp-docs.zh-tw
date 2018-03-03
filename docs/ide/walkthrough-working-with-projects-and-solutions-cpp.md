---
title: "逐步解說： 使用專案和方案 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 12/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a20c0ee933d49465a841b638a8260181d7175ac5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>逐步解說：使用專案和方案 (C++)

以下說明如何在 Visual Studio 中建立 C++ 專案，加入程式碼，然後建置並執行專案。 本逐步解說中的專案是追蹤有多少玩家正在進行不同的撲克牌遊戲的程式。

在 Visual Studio 中，工作被組織在專案和方案。 方案可以包含一個以上專案，例如 DLL 和參考此 DLL 的可執行檔。 如需詳細資訊，請參閱[方案和專案](/visualstudio/ide/solutions-and-projects-in-visual-studio)。

## <a name="before-you-start"></a>開始之前

若要完成此逐步解說，您會需要 Visual Studio 2017 版本 15.3 或更新版本。 如果您需要的複本，以下是簡短的指南：[安裝 c + + 支援 Visual Studio 中的](../build/vscpp-step-0-installation.md)。 如果您沒尚未完成，請依照下一步 透過"Hello，World"教學課程，並確定已正確安裝 Visual c + + 及它的安裝後運作。

如果您了解 c + + 語言的基本概念，知道什麼編譯器、 連結器及偵錯工具可用來，它可幫助。 本教學課程也會假設您熟悉 Windows，以及如何使用功能表、 對話方塊

## <a name="create-a-project"></a>建立專案

若要建立專案，請先選擇專案類型範本。 針對每個專案類型中，Visual Studio 設定編譯器設定與 — 根據類型 — 產生稍後可以修改的起始程式碼。

### <a name="to-create-a-project"></a>若要建立專案

1. 在功能表列上選擇 **檔案 > 新增 > 專案**。

1. 在左窗格中**新專案**對話方塊方塊中，展開 **已安裝**選取**Visual c + +**，如果尚未開啟。

1. 在中間窗格內的已安裝的範本清單中，選取**Windows 主控台應用程式**。

1. 輸入中的專案名稱**名稱**方塊。 針對此範例中，輸入**遊戲**。

   您可以接受預設位置中的**位置**下拉式清單中，輸入不同的位置，或選擇**瀏覽**按鈕瀏覽至您要儲存專案的目錄。

   當您建立專案時，Visual Studio 會將專案放在方案中。 根據預設，方案的名稱與專案名稱相同， 您可以變更在名稱**方案名稱**方塊中，但此範例中，保留預設名稱。

1. 選擇 [確定] 按鈕以建立專案。

   Visual Studio 會建立您的新方案和專案檔，並開啟它所產生的 Game.cpp 原始程式檔的編輯器。

## <a name="organize-projects-and-files"></a>專案和檔案組織

您可以使用**方案總管 中**來組織及管理專案、 檔案和您的方案中的其他資源。

本逐步解說的這個部分說明如何將類別加入至專案。 當您新增的類別時，Visual Studio 會加入對應的.h 和.cpp 檔案。 您可以看到結果**方案總管 中**。

### <a name="to-add-a-class-to-a-project"></a>若要將類別加入至專案

1. 如果**方案總管 中**視窗不會顯示在 Visual Studio 功能表列上，選擇**檢視 > 方案總管 中**。

1. 在**方案總管 中**，選取**遊戲**專案。 在功能表列上選擇 **專案 > 加入類別**。

1. 在**加入類別** 對話方塊中，輸入*Cardgame*中**類別名稱**方塊。 不要修改預設檔案名稱及設定。 選擇 [確定]  按鈕。

   Visual Studio 建立新的檔案，並將它們加入至您的專案。 您可以看到它們在**方案總管 中**視窗。 Cardgame.h 和 Cardgame.cpp 檔案會在編輯器中開啟。

1. 編輯 Cardgame.h 檔案，並進行這些變更：

   - 在類別定義的左邊大括號後面加入兩個私用資料成員。
      <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - 修改 Visual Studio 產生的預設建構函式。 在 `public:` 存取規範之後，尋找如下所示的程式碼行：

      `Cardgame();`

      修改此建構函式，以採用一個參數的型別`int`具名*玩家*。

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - 在預設解構函式之後加入的內嵌宣告`static int`成員函式，名為*GetParticipants*不採用任何參數，並傳回`totalParticipants`值。

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   在您變更之後，Cardgame.h 檔案應類似於：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->
   ```cpp
   #pragma once
   class Cardgame
   {
       int players;
       static int totalParticipants;
   public:
       Cardgame(int players);
       ~Cardgame(void);
       static int GetParticipants() { return totalParticipants; }
   };
   ```

   線條`#pragma once`會告訴編譯器包含標頭檔一次。 如需詳細資訊，請參閱[一旦](../preprocessor/once.md)。 此標頭檔中其他 c + + 關鍵字的詳細資訊，請參閱[類別](../cpp/class-cpp.md)， [int](../cpp/fundamental-types-cpp.md)，[靜態](../cpp/storage-classes-cpp.md)，和[公用](../cpp/public-cpp.md)。

1. 選擇**Cardgame.cpp**  索引標籤頂端的 編輯 窗格來開啟它進行編輯。

1. 刪除檔案的所有內容並取代為下列程式碼：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->
   ```cpp
   #include "stdafx.h"
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
   > 輸入程式碼時，您可以使用自動完成。 例如，如果您輸入在鍵盤上的這段程式碼，您可以輸入*pl*或*tot 後*然後按下 Ctrl + 空格鍵。 自動完成輸入`players`或`totalParticipants`您。

## <a name="add-test-code-to-your-main-function"></a>將測試程式碼加入至 main 函式

將一些程式碼加入至您測試新的函式的應用程式。

### <a name="to-add-test-code-to-the-project"></a>將測試程式碼加入至專案

1. 在 [Game.cpp 編輯器] 視窗中，取代現有的程式碼與這個：

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->
   ```cpp
   // Game.cpp : Defines the entry point for the console application.
   //

   #include "stdafx.h"
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
這個程式碼加入測試函式， `PlayGames`、 原始碼和呼叫在`main`。 

## <a name="build-and-run-your-app-project"></a>建置並執行應用程式專案

接下來，建置專案，並執行應用程式。

### <a name="to-build-and-run-the-project"></a>若要建置及執行專案

1. 在功能表列上，選擇 [建置] > [建置解決方案]。

   從組建輸出會顯示在**輸出**視窗。 如果建置成功，輸出應該看起來像這樣：

   ```Output
   1>------ Build started: Project: Game, Configuration: Debug Win32 ------
   1>  stdafx.cpp
   1>  Game.cpp
   1>  Cardgame.cpp
   1>  Generating Code...
   1>  Game.vcxproj -> C:\Users\username\Source\Repos\Game\Debug\Game.exe
   ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
   ```

   **輸出**視窗可以顯示不同的步驟，視組建組態而定，但若專案建置成功，最後一行應該與相似所顯示的輸出。

   如果您的組建並未成功，比較您在前面步驟所示的程式碼的程式碼。

1. 若要執行專案，在功能表列上，選擇 **偵錯 > 啟動但不偵錯**。 主控台視窗應該會出現，並輸出應該會與以下相似：

   ```Output
   4 players have started a new game.  There are now 4 players in total.
   8 players have started a new game.  There are now 12 players in total.
   1 players have started a new game.  There are now 13 players in total.
   5 players have started a new game.  There are now 18 players in total.
   ```
請按任一按鍵關閉主控台視窗。

恭喜，您已成功建立應用程式專案和方案。 若要深入了解如何建置 c + + 程式碼專案，Visual Studio 中的繼續本逐步解說。

## <a name="next-steps"></a>後續步驟

**上一步：** [使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
**下一步:** [逐步解說： 建置專案 （c + +）](../ide/walkthrough-building-a-project-cpp.md)。

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)  
[建置 C/C++ 程式](../build/building-c-cpp-programs.md)