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
ms.openlocfilehash: b5f2b6dd56d3a755ee73058c024152e12157a6bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501951"
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++ 中的 MBCS 支援

在已啟用 MBCS 的 Windows 版本上執行時, 視覺化C++開發系統 (包括整合式原始程式碼編輯器、偵錯工具和命令列工具) 是啟用 mbcs 的功能, 但記憶體視窗除外。

記憶體視窗不會將資料的位元組解譯為 MBCS 字元，不過能解譯為 ANSI 或 Unicode 字元 ANSI 字元固定為 1 個位元組大小，而 Unicode 字元則是 2 個位元組大小。 使用 MBCS 時，字元可以是 1 個或 2 個位元組大小，解譯則是根據所使用的字碼頁而定。 因此，記憶體視窗很難順利顯示 MBCS 字元， 記憶體視窗不知道哪個位元組是字元的開頭。 開發人員可以在 [記憶體] 視窗中查看位元組值, 並查詢資料表中的值, 以決定字元標記法。 這是可行的, 因為開發人員知道以原始程式碼為基礎之字串的起始位址。

視覺C++效果會接受雙位元組字元, 無論其適用於何處。 這包括對話方塊中的路徑名稱和檔案名, 以及視覺效果C++資源編輯器中的文字專案 (例如, 對話方塊編輯器中的靜態文字和圖示編輯器中的靜態文字專案)。 此外, 預處理器會辨識一些雙位元組指示詞 (例如, 語句中`#include`的檔案名), 以及做為和`data_seg` pragma `code_seg`的引數。 在原始程式碼編輯器中, 會接受批註和字串常值中的雙位元組字元, 但不會在 CC++ /language 元素中 (例如變數名稱)。

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>支援輸入法編輯器 (IME)

針對使用 MBCS 的東亞市場所撰寫的應用程式 (例如日本) 通常會支援同時輸入單一和雙位元組字元的 Windows 輸入法。 視覺化C++開發環境包含對 IME 的完整支援。

日文鍵盤不直接支援中文字元。 IME 會將語音字串 (以其中一個其他日文字母 (Romaji、片假名或平假名) 輸入) 轉換成其可能的漢字標記法。 如果有不明確的情況, 您可以從數個替代專案中選取。 當您選取了預定的中文字元時, 輸入法會`WM_CHAR`將兩則訊息傳遞至控制應用程式。

由 ALT +\`按鍵組合啟動的 IME 會顯示為一組按鈕 (指標) 和轉換視窗。 應用程式會將視窗置於文字插入點。 應用程式必須藉`WM_MOVE`由`WM_SIZE`重新置放轉換視窗來處理和訊息, 以符合目標視窗的新位置或大小。

如果您想要讓應用程式的使用者能夠輸入中文字元, 應用程式必須處理 Windows 輸入法訊息。 如需有關輸入法程式設計的詳細資訊, 請參閱[輸入方法管理員](/windows/win32/intl/input-method-manager)。

## <a name="visual-c-debugger"></a>Visual C++偵錯工具

Visual C++偵錯工具提供在輸入法訊息上設定中斷點的功能。 此外, [記憶體] 視窗也可以顯示雙位元組字元。

## <a name="command-line-tools"></a>命令列工具

視覺化C++的命令列工具, 包括編譯器、NMAKE 和資源編譯器 (RC。EXE), 已啟用 MBCS。 編譯應用程式的資源時, 您可以使用資源編譯器的/c 選項來變更預設的字碼頁。

若要在原始碼編譯時間變更預設地區設定, 請使用[#pragma setlocale](../preprocessor/setlocale.md)。

## <a name="graphical-tools"></a>圖形工具

以 Visual C++ Windows 為基礎的工具 (例如 Spy + + 和資源編輯工具) 完全支援 IME 字串。

## <a name="see-also"></a>另請參閱

[多位元組字元集 (MBCS) 的支援](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS 程式設計提示](../text/mbcs-programming-tips.md)
