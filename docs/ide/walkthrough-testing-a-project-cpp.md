---
title: "逐步解說： 測試專案 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ba928d4a81252b76856273160af63ed8707e7e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-testing-a-project-c"></a>逐步解說：測試專案 (C++)
當您在偵錯模式執行程式時，您可以使用中斷點暫停程式，以檢查變數和物件的狀態。  
  
 在本逐步解說中，您可以監看變數的值所執行的程式，並且推論出值不如預期的原因。  
  
## <a name="prerequisites"></a>必要條件  
  
-   本逐步解說假設您已了解 C++ 語言的基本概念。  
  
-   它也會假設您已完成的稍早相關逐步解說中所列[使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
### <a name="to-run-a-program-in-debug-mode"></a>若要偵錯模式執行程式  
  
1.  開啟 TestGames.cpp 進行編輯。  
  
2.  選取這行程式碼：  
  
     `Cardgame.solitaire(1);`  
  
3.  若要設定中斷點，在該行，功能表列上選擇 **偵錯**，**切換中斷點**，或選擇 F9 鍵。 行的左邊會出現一個紅色圓圈它會指出已設定中斷點。 若要移除中斷點，您可以選擇功能表命令或 F9 鍵一次。  
  
     如果您使用滑鼠，您也可以設定或移除中斷點，左邊界中按一下。  
  
4.  在功能表列上選擇 **偵錯**，**開始偵錯**，或選擇 F5 鍵。  
  
     當程式到達中斷點的程式時，執行會停止，因為您的程式處於中斷模式。 黃色箭號左邊的一行程式碼，表示它是要執行的下一行。  
  
5.  若要檢查的值`Cardgame::totalParticipants`變數，將指標移`Cardgame`然後將它移擴充控制工具提示視窗的左邊。 變數名稱`totalParticipants`並顯示其值為 12。  
  
     開啟快顯功能表`Cardgame::totalParticipants`變數，然後選擇 **加入監看式**顯示在該變數**監看式 1**視窗。 您也可以選取變數，並將它拖曳至**監看式 1**視窗。  
  
6.  若要跳至下一行程式碼，在功能表列上選擇**偵錯**，**不進入函式**，或選擇 F10 鍵。  
  
     值`Cardgame::totalParticipants`中**監看式 1**視窗現在會顯示為 13。  
  
7.  開啟快顯功能表`return 0;`陳述式，然後選擇 **執行至游標處**。 在程式碼左側的黃色箭號會指向下一個陳述式，來執行。  
  
8.  `Cardgame::totalParticipants` Cardgame 終止時，應該降低數字。 此時，`Cardgame::totalParticipants`應該等於 0，因為已刪除所有 Cardgame 執行個體，但**監看式 1**視窗表示`Cardgame::totalparticipants`等於 18。 這表示在程式碼中，您可以偵測並修正藉由完成下一個逐步解說，是 bug[逐步解說： 偵錯專案 （c + +）](../ide/walkthrough-debugging-a-project-cpp.md)。  
  
9. 若要停止程式，在功能表列上，選擇 **偵錯**，**停止偵錯**，或選擇 Shift + F5 鍵盤快速鍵。  
  
## <a name="next-steps"></a>後續步驟  
 **上一步：** [逐步解說： 建置專案 （c + +）](../ide/walkthrough-building-a-project-cpp.md) &#124;**下一步：**[逐步解說： 偵錯專案 （c + +）](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)