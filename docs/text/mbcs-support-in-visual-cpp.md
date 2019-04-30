---
title: Visual C++ 中的 MBCS 支援
ms.date: 11/04/2016
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
ms.openlocfilehash: 3f57e9feac7f129b3fb8653c7b1a2eacb021bf29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410596"
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++ 中的 MBCS 支援

在 Windows 中，視覺效果的 mbcs 的版本上執行時C++（包括整合式原始檔程式碼編輯器、 偵錯工具和命令列工具） 的開發系統是 mbcs 的除了 [記憶體] 視窗。

記憶體視窗不會將資料的位元組解譯為 MBCS 字元，不過能解譯為 ANSI 或 Unicode 字元 ANSI 字元固定為 1 個位元組大小，而 Unicode 字元則是 2 個位元組大小。 使用 MBCS 時，字元可以是 1 個或 2 個位元組大小，解譯則是根據所使用的字碼頁而定。 因此，記憶體視窗很難順利顯示 MBCS 字元， 記憶體視窗不知道哪個位元組是字元的開頭。 開發人員可以在 [記憶體] 視窗中檢視的位元組值，並查閱資料表，判斷字元表示法中的值。 這可能是因為開發人員知道為基礎的原始程式碼字串的起始位址。

視覺化C++接受雙位元組字元，若要這樣做適當的位置。 這包括對話方塊和視覺效果的文字項目中的路徑名稱和檔案名稱C++資源編輯器 （例如，在對話方塊編輯器中靜態文字） 和圖示編輯器中的靜態文字項目。 此外，前置處理器會辨識某些雙位元組指示詞 — 例如，檔案中的名稱`#include`陳述式，並做為引數`code_seg`和`data_seg`pragma。 在 原始程式碼編輯器，在註解和字串常值的雙位元組字元已被接受，雖然不是在 C /C++語言項目 （例如變數的名稱）。

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> 支援的輸入法編輯器 (IME)

通常使用 MBCS （比方說，日本） 的東亞市場支援 Windows IME 輸入這兩個單一位元組和雙位元組字元所撰寫的應用程式。 視覺效果C++開發環境包含之 IME 的完整支援。

日文鍵盤不直接支援漢字字元。 IME 轉換注音標示的字串，其中一種其他日文字母 （羅馬字母、 片假名或平假名） 進入其可能的漢字表示。 如果有模稜兩可，您可以選取從多個替代方案。 當您選取想要的漢字字元時，輸入法會傳遞兩個`WM_CHAR`控制的應用程式的訊息。

輸入法，由 ALT + 啟動\`按鍵組合，會顯示為一組按鈕 （指標） 和轉換 視窗。 應用程式將放置在文字插入點的視窗。 應用程式必須處理`WM_MOVE`和`WM_SIZE`透過重新定位 [轉換] 視窗的訊息以符合新的位置或目標視窗的大小。

如果您想要能夠輸入日文漢字字元的應用程式的使用者，應用程式必須處理 Windows IME 訊息。 如需輸入法程式設計的詳細資訊，請參閱[輸入法管理員](/windows/desktop/intl/input-method-manager)。

## <a name="visual-c-debugger"></a>視覺化C++偵錯工具

視覺效果C++偵錯工具讓您能夠輸入法的訊息上設定中斷點。 此外，[記憶體] 視窗可以顯示雙位元組字元。

## <a name="command-line-tools"></a>命令列工具

視覺效果C++命令列工具，包括編譯器、 NMAKE 和資源編譯器 (RC。EXE) 中，MBCS 啟用。 您可以使用資源編譯器 /c 選項來編譯應用程式的資源時變更的預設字碼頁。

若要變更預設的地區設定，在來源的程式碼編譯時期，請使用[#pragma setlocale](../preprocessor/setlocale.md)。

## <a name="graphical-tools"></a>圖形化工具

視覺效果C++以 Windows 為基礎的工具，例如 Spy + + 和資源的編輯工具，完全支援的輸入法的字串。

## <a name="see-also"></a>另請參閱

[多位元組字元集 (MBCS) 的支援](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS 程式設計提示](../text/mbcs-programming-tips.md)
