---
title: 逐步解說： 偵錯專案 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecfda5e2549b3aa9be1f0471e301cc2a21c6fd5a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-debugging-a-project-c"></a>逐步解說：偵錯專案 (C++)
在這個逐步解說中，您會修改程式以修正在測試專案時所發現的問題。  
  
## <a name="prerequisites"></a>必要條件  
  
-   本逐步解說假設您已了解 C++ 語言的基本概念。  
  
-   它也會假設您已完成的稍早相關逐步解說中所列[使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
### <a name="to-fix-a-program-that-has-a-bug"></a>若要修正 bug 的程式  
  
1.  若要查看 `Cardgame` 物件被終結時發生什麼事，請檢視 `Cardgame` 類別的解構函式。  
  
     在功能表列上選擇 **檢視**，**類別檢視**。  
  
     在**類別檢視**視窗中，展開 **遊戲**專案樹狀結構並選取**Cardgame**類別來顯示類別成員和方法。  
  
     開啟快顯功能表 **~Cardgame(void)** 解構函式，然後選擇 **移至定義**。  
  
2.  若要在 Cardgame 終止時減少 `totalParticipants`，請在 `Cardgame::~Cardgame` 解構函式的左邊和右邊大括號之間加入下列程式碼。  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
3.  Cardgame.cpp 檔案應該會與以下相似之後加以變更：  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
4.  在功能表列上，選擇 [建置] 、[建置方案] 。  
  
5.  當建置完成時，執行以偵錯模式選擇**偵錯**，**開始偵錯**功能表列上，或是選擇 F5 鍵。 程式會在第一個中斷點上暫停。  
  
6.  若要逐步執行程式，請在功能表列中，選擇 **偵錯**，**不進入函式**，或選擇 F10 鍵。  
  
     請注意，在每個 Cardgame 建構函式執行後，`totalParticipants` 的值都會增加。 當 `PlayGames` 函式返回時，因為每個 Cardgame 執行個體會超出範圍和被刪除 (和呼叫解構函式)，`totalParticipants` 會減少。 之前`return`執行陳述式，`totalParticipants`等於 0。  
  
7.  繼續逐步執行程式直到程式結束，或讓它執行選擇**偵錯**，**執行**功能表列上，或是選擇 F5 鍵。  
  
## <a name="next-steps"></a>後續步驟  
 **上一步：** [逐步解說： 測試專案 （c + +）](../ide/walkthrough-testing-a-project-cpp.md) &#124; **下一步：**[逐步解說： 部署程式 （c + +）](../ide/walkthrough-deploying-your-program-cpp.md)  
  
## <a name="see-also"></a>另請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)