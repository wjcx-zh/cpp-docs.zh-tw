---
title: "逐步解說：使用專案和方案 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "專案 [C++]"
  - "專案 [C++], 關於專案"
  - "方案 [C++]"
  - "方案 [C++], 關於方案"
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：使用專案和方案 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下說明如何在 Visual Studio 中建立 C\+\+ 專案，加入程式碼，然後建置並執行專案。  本逐步解說中的專案是追蹤有多少玩家正在進行不同的撲克牌遊戲的程式。  
  
 在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中，工作是組織在專案和方案中。  方案可以包含一個以上專案，例如 DLL 和參考此 DLL 的可執行檔。  如需詳細資訊，請參閱[專案和方案](../Topic/Solutions%20and%20Projects%20in%20Visual%20Studio.md)。  
  
## 必要條件  
  
-   若要完成此逐步解說，您必須了解 C\+\+ 語言的基礎。  
  
## 建立專案  
 若要建立專案，請先選擇專案類型範本。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 會針對每個專案類型，設定編譯器設定，並根據類型產生稍後可以修改的起始程式碼。  
  
#### 若要建立專案  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊的左窗格中，依序展開 \[**已安裝的範本**\] 節點、\[**Visual C\+\+**\] 節點，然後選取 \[**Win32**\]。  
  
3.  在中間窗格的已安裝的範本清單中，選取 \[**Win32 主控台應用程式**\]。  
  
4.  在 \[**名稱**\] 方塊中輸入專案名稱。  在本範例中，請輸入「遊戲」。  
  
     您可以接受 \[**位置**\] 下拉式清單的預設位置，輸入其他位置，或選擇 \[**瀏覽**\] 按鈕瀏覽至您要儲存專案的目錄。  
  
     當您建立專案時，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 會將此專案放入方案中。  根據預設，方案的名稱與專案名稱相同，  您可以變更 \[**方案名稱**\] 方塊中的名稱，但在本範例中，請保留預設名稱。  
  
     選擇 \[**確定**\] 按鈕啟動 \[**Win32 應用程式精靈**\]。  
  
5.  在 \[**Win32 應用程式精靈**\] 對話方塊的 \[**概觀**\] 頁面上選擇 \[**下一步**\] 按鈕。  
  
6.  在 \[**應用程式設定**\] 頁面的 \[**應用程式類型**\] 下，選取 \[**主控台應用程式**\]。  清除 \[**其他選項**\] 底下的 \[**先行編譯標頭檔**\] 設定，然後選取 \[**空專案**\] 設定。  選擇 \[**完成**\] 按鈕以建立專案。  
  
     您現在擁有的是尚未有原始程式碼檔案的專案。  
  
## 組織方案中的專案及檔案  
 您可以使用 \[**方案總管**\] 來組織並管理方案中的專案、檔案及其他資源。  
  
 本逐步解說的這個部分說明如何將類別加入至專案。  當您加入類別時，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 會加入對應的 .h 和 .cpp 檔案。  接下來，為測試類別的主程式加入新的原始程式碼檔。  
  
#### 若要將類別加入至專案  
  
1.  如果 \[**方案總管**\] 未顯示，請在功能表列上選擇 \[**檢視**\]、\[**方案總管**\]。  
  
2.  在 \[**方案總管**\] 中，開啟 \[**標頭檔**\] 資料夾的捷徑功能表，然後選擇 \[**加入**\]、\[**類別**\]。  
  
     在 \[**加入類別**\] 對話方塊的左窗格中，展開 \[**Visual C\+\+**\] 節點並選取 \[**C\+\+**\]，然後在中間窗格的已安裝的範本清單中選取 \[**C\+\+ 類別**\]。  選擇 \[**加入**\] 按鈕。  
  
3.  在 \[**泛型 C\+\+ 類別精靈**\] 的 \[**類別名稱**\] 方塊中輸入 Cardgame。  不要修改預設檔案名稱及設定。  選擇 \[**完成**\] 按鈕。  
  
4.  Cardgame.h 檔案會在編輯器中開啟。  進行下列變更：  
  
    -   在類別定義的左邊大括號後面加入兩個私用資料成員。  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)]  
  
    -   修改 Visual Studio 產生的預設建構函式。  在 `public:` 存取規範之後，尋找如下所示的程式碼行：  
  
         `Cardgame(void);`  
  
         將其修改成接受一個屬於 `int` 類型、名為 players 的參數。  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]  
  
    -   在預設解構函式之後，加入靜態整數成員函式 \(名稱為 GetParticipants\) 的內嵌宣告，這個函式不接受參數，但會傳回 totalParticipants 值。  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]  
  
5.  在您變更之後，Cardgame.h 檔案應類似於：  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]  
  
     程式行 `#pragma once` 指示編譯器只包含檔案一次。  如需詳細資訊，請參閱 [once](../preprocessor/once.md)。  
  
     如需這個標頭檔中其他 C\+\+ 關鍵字的詳細資訊，請參閱 [class](../cpp/class-cpp.md)、[int](../cpp/fundamental-types-cpp.md)、[static](../misc/static-cpp.md) 和 [public](../cpp/public-cpp.md)。  
  
6.  選擇編輯窗格中的 \[**Cardgame.cpp**\] 索引標籤以開啟檔案進行編輯。  
  
7.  刪除檔案的所有內容並取代為下列程式碼：  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]  
  
    > [!NOTE]
    >  輸入程式碼時，您可以使用自動完成。  例如，如果您輸入這個程式碼，您可以輸入 pl 或 tot 後再按 Ctrl\+Spacebar，讓自動完成替您完成 `players` 或 `totalParticipants` 的輸入。  
  
     如需 `#include` 的詳細資訊，請參閱 [\#include 指示詞](../preprocessor/hash-include-directive-c-cpp.md)。  
  
## 加入原始程式檔  
 現在，加入原始程式碼檔，做為測試類別的主程式。  
  
#### 若要加入新的原始程式檔  
  
1.  在 \[**方案總管**\] 中，開啟 \[**原始程式檔**\] 資料夾的捷徑功能表，然後選擇 \[**加入**\]、\[**新增項目**\]。  
  
     在 \[**加入新項目**\] 對話方塊的左窗格中，依序展開 \[**已安裝的**\] 節點、\[**Visual C\+\+**\] 節點，然後選取 \[**程式碼**\]。  在中間窗格中，選取 \[**C\+\+ 檔 \(.cpp\)**\]。  
  
2.  在 \[**名稱**\] 文字方塊中輸入 TestGames.cpp，然後選擇 \[**新增**\] 按鈕。  
  
3.  在 TestGames.cpp 編輯視窗中，輸入下列程式碼。  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]  
  
## 建置並執行專案  
 現在建置專案並執行應用程式。  
  
#### 若要建置及執行專案  
  
1.  在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
    > [!NOTE]
    >  如果您使用的 Express 版未顯示 \[**建置**\] 功能表，請在功能表列上，選取 \[**工具**\]、\[**設定**\]、\[**專家設定**\] 啟用它。  
  
     建置的輸出會顯示在 \[**輸出**\] 視窗中。  如果建置成功，輸出應該看起來像這樣：  
  
  **1\>\-\-\-\-\-\- 已開始建置: 專案: Game, 組態: Debug Win32 \-\-\-\-\-\-**  
**1\>  TestGames.cpp**  
**1\>  Cardgame.cpp**  
**1\>  正在產生程式碼...**  
**1\>  Game.vcxproj \-\> c:\\users\\username\\documents\\visual studio\\Projects\\Game\\Debug\\Game.exe**  
**\=\=\=\=\=\=\=\=\=\= 建置: 1 成功、0 失敗、0 最新狀態、0 略過 \=\=\=\=\=\=\=\=\=\=**     \[**輸出**\] 視窗可能顯示不同的步驟，視版本和組建組態而定。但若專案建置成功，最後一行應該與顯示的輸出相似。  
  
     如果建置失敗，請將您的程式碼與在前面步驟中提供的程式碼做比較。  
  
2.  若要執行專案，請在功能表列上選擇 \[**偵錯**\]、\[**啟動但不偵錯**\]。  輸出應該會與以下相似：  
  
  **4 個玩家已開始新的遊戲。現在總共有 4 個玩家。**  
**8 個玩家已開始新的遊戲。現在總共有 12 個玩家。**  
**1 個玩家已開始新的遊戲。現在總共有 13 個玩家。**  
**5 個玩家已開始新的遊戲。現在總共有 18 個玩家。**  
  
## 後續步驟  
 **上一個主題**：[使用 Visual Studio IDE 進行 C\+\+ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  **下一個主題**：[逐步解說：建置專案 \(C\+\+\)](../ide/walkthrough-building-a-project-cpp.md)。  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)