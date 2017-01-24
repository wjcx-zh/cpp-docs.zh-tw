---
title: "逐步解說：測試專案 (C++) | Microsoft Docs"
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
  - "專案測試 [C++]"
  - "專案 [C++], 測試"
  - "測試專案"
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：測試專案 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在偵錯模式中執行程式時，可使用中斷點來暫停程式，以檢查變數和物件的狀態。  
  
 在此逐步解說中，您會在程式執行時監看某個變數的值，並推斷變數值不在預期之中的原因。  
  
## 必要條件  
  
-   本逐步解說假設您已了解 C\+\+ 語言的基礎。  
  
-   它也會假設，您已完成[使用 Visual Studio IDE 進行 C\+\+ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中所列的先前的相關逐步解說。  
  
### 若要在偵錯模式中執行程式  
  
1.  開啟要編輯的 TestGames.cpp。  
  
2.  選擇這一行程式碼：  
  
     `Cardgame.solitaire(1);`  
  
3.  若要在該行設定中斷點，請在功能表列上選擇 \[**偵錯**\]、\[**切換中斷點**\]，或選擇 F9 鍵。  程式碼左邊會出現一個紅色圓圈，表示設定了中斷點。  若要移除中斷點，您可以再次選擇功能表命令或 F9 鍵。  
  
     如果您使用滑鼠，您也可以按一下左邊界來設定或移除中斷點。  
  
4.  在功能表列上，選擇 \[**偵錯**\]、\[**開始偵錯**\]，或選擇 F5 鍵。  
  
     當程式執行到設有中斷點的那行程式碼時，就會暫時停止執行 \(因為此時程式處於中斷模式\)。  程式碼行左邊的黃色箭號表示此行是要執行的下一行程式碼。  
  
5.  若要檢查 `Cardgame::totalParticipants` 變數的值，請將游標移至 `Cardgame` 上方，然後再移至工具提示視窗左邊的展開控制項上方。  此時會顯示變數名稱 `totalParticipants` 及其值 12。  
  
     開啟 `Cardgame::totalParticipants` 變數的捷徑功能表，然後選擇 \[**加入監看式**\] 將該變數顯示在 \[**監看式 1**\] 視窗中。  您也可以選取變數，然後將它拖曳至 \[**監看式 1**\] 視窗。  
  
6.  若要前進至下一行程式碼，請在功能表列上選擇 \[**偵錯**\]、\[**不進入函式**\]，或選擇 F10 鍵。  
  
     \[**監看式 1**\] 視窗中的 `Cardgame::totalParticipants` 值現在顯示為 13。  
  
7.  開啟 `return 0;` 陳述式的捷徑功能表，然後選擇 \[**執行至游標處**\]。  程式碼左邊的黃色箭號代表它是接下來要執行的陳述式。  
  
8.  當 Cardgame 結束時，`Cardgame::totalParticipants` 數目應該會減少。  此時，`Cardgame::totalParticipants` 應該等於 0，這是因為所有 Cardgame 執行個體都已經刪除，但 \[**監看式 1**\] 視窗卻指出 `Cardgame::totalparticipants` 等於 18。  這表示程式碼中有 Bug，您可以完成下一個逐步解說[逐步解說：偵錯專案 \(C\+\+\)](../ide/walkthrough-debugging-a-project-cpp.md)，偵測並修正這個錯誤。  
  
9. 若要停止程式，請在功能表列上，選擇 \[**偵錯**\]、\[**停止偵錯**\] 或選擇 Shift\+F5 鍵盤快速鍵。  
  
## 後續步驟  
 **上一個主題：** [逐步解說：建置專案 \(C\+\+\)](../ide/walkthrough-building-a-project-cpp.md) &#124; **下一個主題**：[逐步解說：偵錯專案 \(C\+\+\)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [DELETE\_PENDING\_Building and Debugging](http://msdn.microsoft.com/zh-tw/9f6ba537-5ea0-46fb-b6ba-b63d657d84f1)