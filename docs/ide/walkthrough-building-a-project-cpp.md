---
title: "逐步解說：建置專案 (C++) | Microsoft Docs"
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
  - "建置專案 [C++]"
  - "專案 [C++]，建置"
  - "專案建置 [C++]"
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：建置專案 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在這個逐步解說中，您要刻意在程式碼中加入 Visual C\+\+ 語法錯誤，以便了解編譯錯誤的樣貌及其修正方式。  當您編譯專案時，會有錯誤訊息指出發生了什麼問題以及發生問題的位置。  
  
## 必要條件  
  
-   本逐步解說假設您已了解 C\+\+ 語言的基本概念。  
  
-   同時假設，您已完成先前列於[使用 Visual Studio IDE 進行 C\+\+ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中的相關逐步解說。  
  
### 若要修正編譯錯誤  
  
1.  在 TestGames.cpp 中，刪除最後一行中的分號，讓它看起來像這樣：  
  
     `return 0`  
  
2.  在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
3.  在 \[**錯誤清單**\] 視窗中的訊息指出專案中有建置錯誤。  訊息描述看起來像這樣：  
  
     `error C2143: syntax error : missing ';' before '}'`  
  
     若要檢視這個錯誤的說明資訊，請在 \[**錯誤清單**\] 視窗中反白顯示該錯誤，然後選擇 F1 鍵。  
  
4.  將分號加回到發生語法錯誤的那一行結尾：  
  
     `return 0;`  
  
5.  在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
     \[**輸出**\] 視窗中的訊息顯示專案已成功編譯。  
  
  **1\>\-\-\-\-\-\- 已開始建置: 專案: Game, 組態: Debug Win32 \-\-\-\-\-\-**  
**1\>  TestGames.cpp**  
**1\>  Game.vcxproj \-\> C:\\Users\\\<username\>\\Documents\\Visual Studio *\<version\>*\\Projects\\Game\\Debug\\Game.exe**  
**\=\=\=\=\=\=\=\=\=\= 建置: 1 成功、0 失敗、0 最新狀態、0 略過 \=\=\=\=\=\=\=\=\=\=**  
  
## 後續步驟  
 **上一個主題：** [逐步解說：使用專案和方案 \(C\+\+\)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) &#124; **下一個主題**：[逐步解說：測試專案 \(C\+\+\)](../ide/walkthrough-testing-a-project-cpp.md)  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [DELETE\_PENDING\_Building and Debugging](http://msdn.microsoft.com/zh-tw/9f6ba537-5ea0-46fb-b6ba-b63d657d84f1)