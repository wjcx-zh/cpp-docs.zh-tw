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
ms.openlocfilehash: 404fcee5e48d8db28e56a005f24f8cac5892240e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375785"
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++ 中的 MBCS 支援

在啟用 MBCS 的 Windows 版本上執行時,Visual C++開發系統(包括整合原始碼編輯器、除錯器和命令列工具)將啟用 MBCS,記憶體視窗除外。

記憶體視窗不會將資料的位元組解譯為 MBCS 字元，不過能解譯為 ANSI 或 Unicode 字元 ANSI 字元固定為 1 個位元組大小，而 Unicode 字元則是 2 個位元組大小。 使用 MBCS 時，字元可以是 1 個或 2 個位元組大小，解譯則是根據所使用的字碼頁而定。 因此，記憶體視窗很難順利顯示 MBCS 字元， 記憶體視窗不知道哪個位元組是字元的開頭。 開發人員可以在記憶體視窗中查看位元組值,並在表中查找值以確定字元表示形式。 這是可能的,因為開發人員知道基於原始碼的字串的起始位址。

可視化C++在適當的情況下接受雙位元組字元。 這包括對話框中的路徑名稱和檔名以及 Visual C++ 資源編輯器中的文本條目(例如,對話框編輯器中的靜態文本和圖示編輯器中的靜態文本條目)。 此外,預處理器可識別一些雙位元組指令,例如,語句`#include`中的檔名,以及作為`code_seg``data_seg`和實例的參數。 在原始碼編輯器中,接受註釋和字串文本中的雙位元組位元元,儘管 C/C++語言元素(如變數名稱)中不接受。

## <a name="support-for-the-input-method-editor-ime"></a><a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>支援輸入方法編輯器 (IME)

為使用 MBCS(例如日本)的東亞市場編寫的應用程式通常支援 Windows IME 輸入單位元組和雙位元元元。 可視化C++開發環境包含對IME的完全支援。

日語鍵盤不直接支援漢字字元。 IME 將用其他日語字母(羅馬吉、卡塔卡納或平假名)輸入的拼音字串轉換為其可能的漢字表示形式。 如果存在歧義,可以從多個備選方案中選擇。 選擇預期的漢字字元後,IME 會向控制應用程式傳遞`WM_CHAR`兩條消息。

由 ALT+\`鍵組合啟動的 IME 顯示為一組按鈕(指示器)和轉換視窗。 應用程式將視窗定位在文本插入點。 應用程式必須透過重新定位轉換`WM_MOVE`視窗`WM_SIZE`來處理和消息,以符合目標視窗的新位置或大小。

如果希望應用程式的用戶能夠輸入漢字字元,則應用程式必須處理 Windows IME 消息。 有關 IME 程式設計的詳細資訊,請參考[輸入方法管理員](/windows/win32/intl/input-method-manager)。

## <a name="visual-c-debugger"></a>視覺化C++除錯器

可視化C++調試器提供在IME消息上設置斷點的能力。 此外,記憶體視窗可以顯示雙位元組字元。

## <a name="command-line-tools"></a>命令列工具

VisualC++命令列工具,包括編譯器、NMAKE 和資源編譯器 (RC)。EXE),已啟用 MBCS。 在編譯應用程式的資源時,可以使用資源編譯器的 /c 選項更改預設代碼頁。

要變更原始碼編譯時間的預設區域設定, 請使用[#pragma设置区域设置](../preprocessor/setlocale.md)。

## <a name="graphical-tools"></a>圖像工具

基於 Windows 的可視化 C++工具(如 Spy+ 和資源編輯工具)完全支援 IME 字串。

## <a name="see-also"></a>另請參閱

[多位元組字元集 (MBCS) 的支援](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS 程式設計提示](../text/mbcs-programming-tips.md)
