---
title: "Visual C++ 中的 MBCS 支援 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "亞洲語言 [C++]"
  - "字元集 [C++], 多位元組"
  - "中文字元 [C++]"
  - "程式碼編輯器 [C++], MBCS 支援"
  - "偵錯工具 [C++], MBCS 支援"
  - "雙位元組字元集 [C++]"
  - "IME [C++]"
  - "IME [C++], MBCS"
  - "輸入法 [C++]"
  - "輸入法 [C++], MBCS"
  - "日文字元 [C++]"
  - "漢字字元支援 [C++]"
  - "MBCS [C++], 啟用"
  - "多位元組字元 [C++]"
  - "NMAKE 程式, MBCS 支援"
  - "資源編輯器 [C++], MBCS 支援"
  - "工具 [C++], MBCS 支援"
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Visual C++ 中的 MBCS 支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

執行於支援 MBCS 的 Windows 2000 或 Windows XP 作業系統版本時，Visual C\+\+ 的開發系統 \(包含整合的原始程式碼編輯器、偵錯工具和命令列工具\) 除了記憶體視窗以外，其餘都支援 MBCS。  
  
 記憶體視窗不會將資料的位元組解譯為 MBCS 字元，不過能解譯為 ANSI 或 Unicode 字元。  ANSI 字元大小固定為 1 個位元組，而 Unicode 字元大小為 2 位元組。  使用 MBCS 時，字元可以是 1 個或 2 個位元組大小，而其說明視正在使用中字碼頁而定。  因此，確實地顯示 MBCS 字元記憶體視窗非常困難。  記憶體視窗不知道哪個位元是字元的開頭。  開發人員可以在記憶體視窗中檢視位元組值，並在資料表中查詢值，以判斷字元表示。  這可能是因為開發人員根據原始程式碼，得知字串的開始位址。  
  
 Visual C\+\+ 會在任何適當的時候接受雙位元組字元。  這包括在對話方塊中的路徑名稱和檔案名稱，以及 Visual C\+\+ 資源編輯器的文字項目 \(例如，對話編輯器裡的靜態文字和圖示編輯器裡的靜態文字項目\)。  除此之外，前置處理器 \(Preprocessor\) 辨識一些雙字元組指示詞─例如，`#include` 陳述式裡的檔案名稱，做為 **code\_seg** 和 **data\_seg** 程式的引數。  在原始程式碼編輯器裡，會接受註解和字串常值裡的雙位元組字元，雖然不是在 C\/C\+\+ 語言項目 \(例如變數名稱\) 中。  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> 輸入法 \(IME\) 的支援  
 為使用 MBCS 的東亞市場 \(例如，日本\) 所撰寫的應用程式，通常支援 Windows IME 來輸入單一位元組和雙位元組字元。  Visual C\+\+ 開發環境包含 IME 的完整支援。  如需詳細資訊，請參閱 [IME 範例：示範如何控制 IME 模式和實作 IME 層級 3](http://msdn.microsoft.com/zh-tw/87ebdf65-cef0-451d-a6fc-d5fb64178b14)。  
  
 日語鍵盤並不直接支援漢字字元。  IME 將以其他日文字母 \(Romaji、片假名或平假名\) 輸入的音標字串轉換成可能的漢字表示。  如果有模稜兩可，您可以從許多替代方法裡選擇。  一旦您選定預定的漢字字元之後，IME 會將兩個 `WM_CHAR` 訊息傳遞至控制應用程式。  
  
 IME 是由 ALT\+\` 鍵組合來啟動，以一組按鈕 \(指示器\) 和轉換視窗出現。  應用程式在文字插入點調整視窗。  應用程式必須處理 `WM_MOVE` 和 `WM_SIZE` 訊息，藉著重新調整轉換視窗以遵照新位置或目標視窗的大小。  
  
 如果您要應用程式的使用者能夠輸入漢字字元，應用程式必須處理 Windows IME 訊息。  如需 IME 程式設計的詳細資訊，請參閱[輸入法 \(IME\)](https://msdn.microsoft.com/en-us/library/ms776145.aspx)。  
  
## Visual C\+\+ 偵錯工具  
 Visual C\+\+ 偵錯工具提供在 IME 訊息上設定中斷點的功能。  除此之外，\[記憶體\] 視窗可以顯示雙位元組字元。  
  
## 命令列工具  
 Visual C\+\+ 命令列工具，包括編譯器、NMAKE 和資源編譯器 \(RC.EXE\)，都支援 MBCS。  當您編譯您的應用程式資源時，您可以使用資源編譯器的 \/c 選項來更改預設字碼頁。  
  
 若要在原始程式碼編譯時更改預設地區設定 \(Locale\)，請使用 [\#pragma setlocale](../preprocessor/setlocale.md)。  
  
## 圖形工具  
 Visual C\+\+ 以 Windows 為基礎所開發的工具，例如 Spy\+\+ 和資源編輯工具，完整支援 IME 字串。  
  
## 請參閱  
 [多位元組字元集 \(MBCS\) 的支援](../text/support-for-multibyte-character-sets-mbcss.md)   
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)