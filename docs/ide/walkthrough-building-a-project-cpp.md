---
title: "逐步解說： 建置專案 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 713a74cc889721259ca99f1622ef5e9919edf573
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-building-a-project-c"></a>逐步解說：建置專案 (C++)
在這個逐步解說中，您要刻意在程式碼中加入 Visual C++ 語法錯誤，以便了解編譯錯誤的樣貌及其修正方式。 當您編譯專案時，會有錯誤訊息指出發生了什麼問題以及發生問題的位置。  
  
## <a name="prerequisites"></a>必要條件  
  
-   本逐步解說假設您已了解 C++ 語言的基本概念。  
  
-   它也會假設您已完成的稍早相關逐步解說中所列[使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
### <a name="to-fix-compilation-errors"></a>若要修正編譯錯誤  
  
1.  在 TestGames.cpp 中，刪除最後一行中的分號，讓它看起來像這樣：  
  
     `return 0`  
  
2.  在功能表列上，選擇 [建置] 、[建置方案] 。  
  
3.  中的訊息**錯誤清單**視窗表示專案的建置時發生錯誤。 訊息描述看起來像這樣：  
  
     `error C2143: syntax error : missing ';' before '}'`  
  
     若要檢視有關此錯誤的說明資訊，加上醒目標示在**錯誤清單**視窗，然後選擇 F1 鍵。  
  
4.  將分號加回到發生語法錯誤的那一行結尾：  
  
     `return 0;`  
  
5.  在功能表列上，選擇 [建置] 、[建置方案] 。  
  
     中的訊息**輸出**視窗表示成功編譯專案。  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>  TestGames.cpp  
    1>  Game.vcxproj -> C:\Users\<username>\Documents\Visual Studio <version>\Projects\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
    ```  
  
## <a name="next-steps"></a>後續步驟  
 **上一步：** [逐步解說： 使用專案和方案 （c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) &#124;**下一步：**[逐步解說： 測試專案 （c + +）](../ide/walkthrough-testing-a-project-cpp.md)  
  
## <a name="see-also"></a>另請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)