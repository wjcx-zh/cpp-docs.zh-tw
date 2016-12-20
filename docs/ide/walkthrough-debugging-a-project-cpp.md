---
title: "逐步解說：偵錯專案 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "偵錯專案"
  - "專案偵錯 [C++]"
  - "專案 [C++], 偵錯"
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：偵錯專案 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在這個步驟中，您會修改程式以修正在測試專案時所發現的問題。  
  
## 必要條件  
  
-   本逐步解說假設您已了解 C\+\+ 語言的基礎。  
  
-   它也會假設，您已完成[使用 Visual Studio IDE 進行 C\+\+ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中所列的先前的相關逐步解說。  
  
### 修正有錯誤的程式  
  
1.  若要查看 `Cardgame` 物件被終結發生什麼事，請檢視 `Cardgame` 類別的解構函式。  
  
     在功能表列上選擇 \[**檢視**\]、\[**類別檢視**\]。  
  
     在 \[**類別檢視**\] 視窗中，展開 \[**Game**\] 專案樹狀結構並選取 \[**Cardgame**\] 類別來顯示類別成員和方法。  
  
     開啟 \[**~Cardgame \(void\)**\] 解構函式的捷徑功能表，然後選擇 \[**移至定義**\]。  
  
2.  若要在 Cardgame 終止時減少 `totalParticipants`，請在 `Cardgame::~Cardgame` 解構函式的左邊和右邊大括號之間輸入下列程式碼：  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
3.  在您變更之後，Cardgame.cpp 檔案應類似於：  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
4.  在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
5.  當建置完成時，可以選取 \[**偵錯**\] 、功能表列上的 \[**啟動偵錯**\] ，或是選擇 F5 鍵執行進入偵錯模式。  程式會在第一個中斷點的位置暫停。  
  
6.  要逐步執行程式，請在功能表列上，選擇 \[**偵錯**\]，\[**步驟**\] 或選擇 F10 鍵。  
  
     請注意，在每個 Cardgame 建構函式 \(Constructor\) 執行後，`totalParticipants` 的值都會增加。  當 `PlayGames` 函式傳回，每個 Cardgame 執行個體會超出範圍和被刪除 \(和呼叫解構函式\)，`totalParticipants` 會減少。  在執行 `return` 陳述式之前，`totalParticipants` 等於 0。  
  
7.  逐步執行程式直到程式結束，或選取功能表列上的 \[**偵錯**\]，\[**執行**\] ，或是選擇 F5 鍵執行。  
  
## 後續步驟  
 **上一個主題：** [逐步解說：測試專案 \(C\+\+\)](../ide/walkthrough-testing-a-project-cpp.md) &#124; **下一個主題**：[逐步解說：部署程式 \(C\+\+\)](../ide/walkthrough-deploying-your-program-cpp.md)  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [DELETE\_PENDING\_Building and Debugging](http://msdn.microsoft.com/zh-tw/9f6ba537-5ea0-46fb-b6ba-b63d657d84f1)