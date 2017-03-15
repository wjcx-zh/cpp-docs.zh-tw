---
title: "逐步解說：編譯針對 Visual Studio 中 CLR 的 C++ 程式 | Microsoft Docs"
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
  - "命令列應用程式 [C++], Managed 程式碼"
  - "編譯程式 [C++]"
  - "Managed 程式碼 [C++]"
  - "Visual C++, Managed 程式碼"
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
caps.latest.revision: 40
caps.handback.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：編譯針對 Visual Studio 中 CLR 的 C++ 程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以建立使用 .NET 類別的 Visual C\+\+ 程式，並使用 Visual Studio 開發環境來編譯這些程式。  
  
 針對這個程序，您可以輸入自己的 Visual C\+\+ 程式，或是使用其中一個範例程式。  我們在此程序中使用的範例程式會建立一個名為 textfile.txt 的文字檔，並會將其儲存至專案目錄。  
  
## 必要條件  
 這些主題假設您了解 C\+\+ 語言的基礎。  
  
### 若要使用 Visual Studio 建立新的專案及加入新的原始程式檔  
  
1.  建立新的專案。  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 Visual C\+\+ 專案類型中，按一下 \[**CLR**\]，再按一下 \[**CLR 空專案**\]。  
  
3.  輸入專案名稱。  
  
     根據預設，包含此專案的方案具有與新專案相同的名稱，不過，您也可以輸入不同的名稱。  您可以視需要輸入不同的專案位置。  
  
     按一下 \[**確定**\] 建立新專案。  
  
4.  如果看不見 \[方案總管\]，請按一下 \[**檢視**\] 功能表上的 \[**方案總管**\]。  
  
5.  將新的原始程式檔加入至專案：  
  
    -   以滑鼠右鍵按一下 \[方案總管\] 中的 \[**原始程式檔**\] 資料夾，指向 \[**加入**\]，然後按一下 \[**新增項目**\]。  
  
    -   按一下 \[**C\+\+ 檔 \(.cpp\)**\]，輸入檔案名稱，然後按一下 \[**加入**\]。  
  
     此 **.cpp** 檔會出現在 \[方案總管\] 的 \[**原始程式檔**\] 資料夾中，並且會出現一個附有索引標籤的視窗，供您輸入想要在該檔案中輸入的程式碼。  
  
6.  在 Visual Studio 中，在新建立的索引標籤中按一下，並輸入有效的 Visual C\+\+ 程式，或是複製及貼上其中一個範例程式。  
  
     例如，您可以使用 [如何：寫入文字檔](../dotnet/how-to-write-a-text-file-cpp-cli.md)範例程式 \(位於 \[程式設計手冊\] 的 \[**檔案處理及 I\/O**\] 節點中\)。  
  
     如果您使用範例程式，請注意您會在建立 .NET 物件時使用 `gcnew` ``  關鍵字而非 `new`，而且 `gcnew` 會傳回控制代碼 \(`^`\) 而非指標 \(`*`\)：  
  
     `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
     如需新的 Visual C\+\+ 語法的詳細資訊，請參閱[Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)。  
  
7.  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     \[**輸出**\] 視窗會顯示有關編譯進度的資訊，例如建置記錄檔的位置，以及表示建置狀態的訊息。  
  
     如果您做了變更，並在沒有進行建置的情況下執行程式，便可能會出現表示專案已過期的對話方塊。  如果您要讓 Visual Studio 永遠都使用目前版本的檔案 \(而非在每次建置應用程式時都提示您\)，請在按一下 \[**確定**\] 之前先選取這個對話方塊上的核取方塊。  
  
8.  在 \[**偵錯**\] 功能表上，按一下 \[**啟動但不偵錯**\]。  
  
9. 如果您使用的是範例程式，則執行程式時會顯示一個命令視窗，指出文字檔已經建立。  請按任何按鍵以關閉此命令視窗。  
  
     **textfile.txt** 文字檔現在位於您的專案目錄中。  您可以使用 \[記事本\] 開啟這個檔案。  
  
    > [!NOTE]
    >  選擇空的 CLR 專案範本會自動設定 **\/clr** 編譯器選項。  若要確認這點，請以滑鼠右鍵按一下 \[**方案總管**\] 中的專案，再按一下 \[**屬性**\]，然後核取 \[**組態屬性**\] 之 \[**一般**\] 節點中的 \[**Common Language Runtime 支援**\] 選項。  
  
## 下一步  
 **上一個主題：** [逐步解說：在命令列上編譯原生 C\+\+ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md) &#124; **下一個主題**：[逐步解說：在命令列上編譯 C 程式](../Topic/Walkthrough:%20Compiling%20a%20C%20Program%20on%20the%20Command%20Line.md)  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C\/C\+\+ 程式](../build/building-c-cpp-programs.md)