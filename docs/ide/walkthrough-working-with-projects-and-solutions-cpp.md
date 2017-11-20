---
title: "逐步解說： 使用專案和方案 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6b30cd4885d5fdd65831c8044a088fcb87b52ae3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>逐步解說：使用專案和方案 (C++)
以下說明如何在 Visual Studio 中建立 C++ 專案，加入程式碼，然後建置並執行專案。 本逐步解說中的專案是追蹤有多少玩家正在進行不同的撲克牌遊戲的程式。  
  
 在 Visual Studio 中，工作被組織在專案和方案。 方案可以包含一個以上專案，例如 DLL 和參考此 DLL 的可執行檔。 如需詳細資訊，請參閱[方案和專案](/visualstudio/ide/solutions-and-projects-in-visual-studio)。  
  
## <a name="prerequisites"></a>必要條件  
  
-   若要完成此逐步解說，您必須了解 C++ 語言的基礎。  
  
## <a name="creating-a-project"></a>建立專案  
 若要建立專案，請先選擇專案類型範本。 針對每個專案類型中，Visual Studio 設定編譯器設定與 — 根據類型 — 產生稍後可以修改的起始程式碼。  
  
#### <a name="to-create-a-project"></a>若要建立專案  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在左窗格中**新專案**對話方塊方塊中，展開 **已安裝的範本** 節點，展開  **Visual c + +**節點，然後再選取**Win32**.  
  
3.  在中間窗格內的已安裝的範本清單中，選取**Win32 主控台應用程式**。  
  
4.  輸入中的專案名稱**名稱**方塊。 針對此範例中，輸入**遊戲**。  
  
     您可以接受預設位置中的**位置**下拉式清單中，輸入不同的位置，或選擇**瀏覽**按鈕瀏覽至您要儲存專案的目錄。  
  
     當您建立專案時，Visual Studio 會將專案放在方案中。 根據預設，方案的名稱與專案名稱相同， 您可以變更在名稱**方案名稱**方塊中，但此範例中，保留預設名稱。  
  
     選擇**確定**按鈕以啟動**Win32 應用程式精靈**。  
  
5.  在**概觀**頁面**Win32 應用程式精靈**，選擇**下一步** 按鈕。  
  
6.  在**應用程式設定**頁面的 **應用程式類型**，選取**主控台應用程式**。 在下**其他選項**，清除**先行編譯標頭**設定，然後再選取**空專案**設定。 選擇 [完成]  按鈕以建立專案。  
  
     您現在擁有的是尚未有原始程式碼檔案的專案。  
  
## <a name="organizing-projects-and-files-in-a-solution"></a>組織方案中的專案及檔案  
 您可以使用**方案總管 中**來組織及管理專案、 檔案和您的方案中的其他資源。  
  
 本逐步解說的這個部分說明如何將類別加入至專案。 當您新增的類別時，Visual Studio 會加入對應的.h 和.cpp 檔案。 接下來，為測試類別的主程式加入新的原始程式碼檔。  
  
#### <a name="to-add-a-class-to-a-project"></a>若要將類別加入至專案  
  
1.  如果**方案總管 中**是未顯示，請在功能表列上選擇 **檢視**，**方案總管 中**。  
  
2.  在**方案總管] 中**，開啟捷徑功能表**標頭檔**資料夾，然後選擇 [**新增**，**類別**。  
  
     在左窗格中**加入類別**對話方塊方塊中，展開  **Visual c + +**節點，然後選取**c + +**，然後在中間窗格內的已安裝的範本清單中，選取  **C + + 類別**。 選擇 [ **加入** ] 按鈕。  
  
3.  在**泛型 c + + 類別精靈**，輸入**Cardgame**中**類別名稱**方塊。 不要修改預設檔案名稱及設定。 選擇**完成** 按鈕。  
  
4.  Cardgame.h 檔案會在編輯器中開啟。 進行下列變更：  
  
    -   在類別定義的左邊大括號後面加入兩個私用資料成員。  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)]  
  
    -   修改 Visual Studio 產生的預設建構函式。 在 `public:` 存取規範之後，尋找如下所示的程式碼行：  
  
         `Cardgame(void);`  
  
         將它修改為採用一個參數的型別`int`具名**玩家**。  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]  
  
    -   在預設解構函式之後加入名為靜態整數成員函式的內嵌宣告**GetParticipants**不採用任何參數，並傳回**totalParticipants**值。  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]  
  
5.  在您變更之後，Cardgame.h 檔案應類似於：  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]  
  
     程式行 `#pragma once` 指示編譯器只包含檔案一次。 如需詳細資訊，請參閱[一旦](../preprocessor/once.md)。  
  
     此標頭檔中其他 c + + 關鍵字的詳細資訊，請參閱[類別](../cpp/class-cpp.md)， [int](../cpp/fundamental-types-cpp.md)，[靜態](../cpp/storage-classes-cpp.md)，和[公用](../cpp/public-cpp.md)。  
  
6.  選擇**Cardgame.cpp**  索引標籤中編輯的窗格，即可開啟進行編輯。  
  
7.  刪除檔案的所有內容並取代為下列程式碼：  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]  
  
    > [!NOTE]
    >  輸入程式碼時，您可以使用自動完成。 例如，如果您輸入此程式碼，您可以輸入**pl**或**tot 後**，使完成自動完成，然後按下 Ctrl + 空格鍵輸入`players`或`totalParticipants`您。  
  
     如需有關資訊`#include`，請參閱[#include 指示詞 （C/c + +）](../preprocessor/hash-include-directive-c-cpp.md)。  
  
## <a name="adding-a-source-file"></a>加入原始程式檔  
 現在，加入原始程式碼檔，做為測試類別的主程式。  
  
#### <a name="to-add-a-new-source-file"></a>若要加入新的原始程式檔  
  
1.  在**方案總管] 中**，開啟捷徑功能表**原始程式檔**資料夾，然後選擇 [**新增**，**新項目**。  
  
     在**加入新項目**對話方塊的左窗格中，展開 **已安裝** 節點，展開  **Visual c + +**節點，然後再選取**程式碼**。 在中間窗格中，選取 [C++ 檔 (.cpp)] 。  
  
2.  輸入**TestGames.cpp**中**名稱**方塊，然後再選擇**新增** 按鈕。  
  
3.  在 TestGames.cpp 編輯視窗中，輸入下列程式碼。  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]  
  
## <a name="building-and-running-a-project"></a>建置並執行專案  
 現在建置專案並執行應用程式。  
  
#### <a name="to-build-and-run-the-project"></a>若要建置及執行專案  
  
1.  在功能表列上，選擇 [建置] 、[建置方案] 。  
  
    > [!NOTE]
    >  如果您使用的 Express 版不會顯示**建置**功能表上，在功能表列上的選擇**工具**，**設定**，**專家設定**加以啟用。  
  
     從組建輸出會顯示在**輸出**視窗。 如果建置成功，輸出應該看起來像這樣：  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>  TestGames.cpp  
    1>  Cardgame.cpp  
    1>  Generating Code...  
    1>  Game.vcxproj -> c:\users\username\documents\visual studio\Projects\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
  
    ```  
  
     **輸出**視窗可以顯示不同的步驟，視版本和組建組態，但若專案建置成功，最後一行應該類似所顯示的輸出。  
  
     如果建置失敗，請將您的程式碼與在前面步驟中提供的程式碼做比較。  
  
2.  若要執行專案，請在功能表列上選擇 [偵錯] 、[啟動但不偵錯] 。 輸出應該會與以下相似：  
  
    ```Output  
    4 players have started a new game.  There are now 4 players in total.  
    8 players have started a new game.  There are now 12 players in total.  
    1 players have started a new game.  There are now 13 players in total.  
    5 players have started a new game.  There are now 18 players in total.  
    ```  
  
## <a name="next-steps"></a>後續步驟  
 **上一步：** [使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。 **下一步:**[逐步解說： 建置專案 （c + +）](../ide/walkthrough-building-a-project-cpp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)