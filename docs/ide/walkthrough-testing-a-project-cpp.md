---
title: 逐步解說：測試專案 (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a9455fa9bf3c9f903f5018a1263978913aa35b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333560"
---
# <a name="walkthrough-testing-a-project-c"></a>逐步解說：測試專案 (C++)
當您在 [偵錯] 模式下執行程式時，您可以使用中斷點暫停程式，以檢查變數和物件的狀態。  
  
 在本逐步解說中，您會在程式執行時監看變數值，並推算該值不如預期的原因。  
  
## <a name="prerequisites"></a>必要條件  
  
-   本逐步解說假設您已了解 C++ 語言的基本概念。  
  
-   同時假設，您已完成先前列於[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中的相關逐步解說。  
  
### <a name="to-run-a-program-in-debug-mode"></a>在 [偵錯] 模式下執行程式  
  
1.  開啟要編輯的 TestGames.cpp。  
  
2.  選取這行程式碼：  
  
     `Cardgame.solitaire(1);`  
  
3.  若要在該行設定中斷點，請在功能表列上，選擇 [偵錯]、[切換中斷點]，或選擇 F9 鍵。 行左邊會出現一個紅色圓圈，表示已設定中斷點。 若要移除中斷點，您可以選擇功能表命令，或再選擇一次 F9 鍵。  
  
     如果您使用滑鼠，您也可以按一下左邊界來設定或移除中斷點。  
  
4.  在功能表列上，選擇 [偵錯]、[開始偵錯]，或選擇 F5 鍵。  
  
     當程式到達具有中斷點的行時，執行會暫時停止，因為您的程式處於 [中斷] 模式。 程式碼行左邊的黃色箭號表示它是要執行的下一行。  
  
5.  若要檢查 `Cardgame::totalParticipants` 變數的值，請將指標移至 `Cardgame` 上方，然後移至工具提示視窗左邊的展開控制項上方。 變數名稱 `totalParticipants` 及其值 12 隨即顯示。  
  
     開啟 `Cardgame::totalParticipants` 變數的捷徑功能表，然後選擇 [新增監看式] 以在 [監看式 1] 視窗中顯示該變數。 您也可以選取變數，然後將它拖曳至 [監看式 1] 視窗。  
  
6.  若要跳到下一行程式碼，請在功能表列上，選擇 [偵錯]、[不進入函式]，或選擇 F10 鍵。  
  
     [監看式 1] 視窗中的 `Cardgame::totalParticipants` 值現在會顯示為 13。  
  
7.  開啟 `return 0;` 陳述式的捷徑功能表，然後選擇 [執行至游標處]。 程式碼左邊的黃色箭號會指向要執行的下一個陳述式。  
  
8.  當 Cardgame 終止時，`Cardgame::totalParticipants` 數目應該會減少。 此時，`Cardgame::totalParticipants` 應該等於 0，因為已刪除所有 Cardgame 執行個體，但 [監看式 1] 視窗表示 `Cardgame::totalparticipants` 等於 18。 這表示程式碼中出現 Bug，您可以完成下一個逐步解說進行偵測及修正：[逐步解說：偵錯專案 (C++)](../ide/walkthrough-debugging-a-project-cpp.md)。  
  
9. 若要停止程式，請在功能表列上，選擇 [偵錯]、[停止偵錯]，或選擇 Shift+F5 鍵盤快速鍵。  
  
## <a name="next-steps"></a>後續步驟  
 **上一步：** [逐步解說：建置專案 (C++)](../ide/walkthrough-building-a-project-cpp.md) &#124; **下一步：**[逐步解說：偵錯專案 (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>請參閱  
 [C++ 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)