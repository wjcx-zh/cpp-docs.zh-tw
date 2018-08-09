---
title: Visual c + + 中的 MBCS 支援 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d00495f95b3c67e4a6fc3613b949b8ae2946bd6
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010382"
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++ 中的 MBCS 支援
是 MBCS 啟用舊版 Windows 上執行時，Visual c + + 開發系統 （包括整合式原始檔程式碼編輯器、 偵錯工具和命令列工具） 已 MBCS 啟用，除了 [記憶體] 視窗。  
  
 記憶體視窗不會將資料的位元組解譯為 MBCS 字元，不過能解譯為 ANSI 或 Unicode 字元 ANSI 字元固定為 1 個位元組大小，而 Unicode 字元則是 2 個位元組大小。 使用 MBCS 時，字元可以是 1 個或 2 個位元組大小，解譯則是根據所使用的字碼頁而定。 因此，記憶體視窗很難順利顯示 MBCS 字元， 記憶體視窗不知道哪個位元組是字元的開頭。 開發人員可以在 [記憶體] 視窗中檢視的位元組值，並查閱資料表，判斷字元表示法中的值。 這可能是因為開發人員知道為基礎的原始程式碼字串的起始位址。  
  
 若要這樣做適當的位置，visual c + + 會接受雙位元組字元。 此對話方塊和 Visual c + + 資源編輯器 （例如，在對話方塊編輯器中靜態文字） 和圖示編輯器中的靜態文字項目中的文字項目中包含路徑名稱和檔案名稱。 此外，前置處理器會辨識某些雙位元組指示詞 — 例如，檔案中的名稱`#include`陳述式，並做為引數`code_seg`和`data_seg`pragma。 在 原始程式碼編輯器，在註解和字串常值的雙位元組字元已被接受，雖然不是在 C/c + + 語言項目 （例如變數的名稱）。  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> 支援的輸入法編輯器 (IME)  
 通常使用 MBCS （比方說，日本） 的東亞市場支援 Windows IME 輸入這兩個單一位元組和雙位元組字元所撰寫的應用程式。 Visual c + + 開發環境包含之 IME 的完整支援。 如需詳細資訊，請參閱 <<c0> [ 輸入法範例： 示範如何控制輸入法模式和實作 IME 層級 3](http://msdn.microsoft.com/87ebdf65-cef0-451d-a6fc-d5fb64178b14)。  
  
 日文鍵盤不直接支援漢字字元。 IME 轉換注音標示的字串，其中一種其他日文字母 （羅馬字母、 片假名或平假名） 進入其可能的漢字表示。 如果有模稜兩可，您可以選取從多個替代方案。 當您選取想要的漢字字元時，輸入法會傳遞兩個`WM_CHAR`控制的應用程式的訊息。  
  
 輸入法，由 ALT + 啟動\`按鍵組合，會顯示為一組按鈕 （指標） 和轉換 視窗。 應用程式將放置在文字插入點的視窗。 應用程式必須處理`WM_MOVE`和`WM_SIZE`透過重新定位 [轉換] 視窗的訊息以符合新的位置或目標視窗的大小。  
  
 如果您想要能夠輸入日文漢字字元的應用程式的使用者，應用程式必須處理 Windows IME 訊息。 如需輸入法程式設計的詳細資訊，請參閱[輸入法編輯器](https://msdn.microsoft.com/library/ms776145.aspx)。  
  
## <a name="visual-c-debugger"></a>Visual c + + 偵錯工具  
 Visual c + + 偵錯工具讓您能夠輸入法的訊息上設定中斷點。 此外，[記憶體] 視窗可以顯示雙位元組字元。  
  
## <a name="command-line-tools"></a>命令列工具  
 Visual c + + 命令列工具，包括編譯器、 NMAKE 和資源編譯器 (RC。EXE) 中，MBCS 啟用。 您可以使用資源編譯器 /c 選項來編譯應用程式的資源時變更的預設字碼頁。  
  
 若要變更預設的地區設定，在來源的程式碼編譯時期，請使用[#pragma setlocale](../preprocessor/setlocale.md)。  
  
## <a name="graphical-tools"></a>圖形化工具  
 Visual c + + Windows 型工具，例如 Spy + + 和資源的編輯工具，完全支援輸入法的字串。  
  
## <a name="see-also"></a>另請參閱  
 [針對多位元組字元集 (Mbcs) 支援](../text/support-for-multibyte-character-sets-mbcss.md)   
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)