---
title: /QIfist (抑制 _ftol)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 5d6e12a1003ea125b0da4bfef580d8096e97553a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336106"
---
# <a name="qifist-suppress-_ftol"></a>/QIfist (抑制 _ftol)

已被取代。 在必須從浮點類型轉換為整數類型時，抑制對 Helper 函式 `_ftol` 的呼叫。

## <a name="syntax"></a>語法

```
/QIfist
```

## <a name="remarks"></a>備註

> [!NOTE]
> **/QIfist**僅在針對 x86 的編譯器中可用;針對 x64 或 ARM 的編譯器中不提供此編譯器選項。

除了從浮點類型轉換為積分類型外,`_ftol`該函數還通過設置控制字位 10 和 11 來確保浮點單元 (FPU) 的舍入模式朝零(截斷) 方向發展。 這保證了從浮點類型轉換為積分類型發生,如 ANSI C 標準所述(放棄數位的小數部分)。 使用 **/QIfist 時**,此保證不再適用。 進一個模式將是英特爾參考手冊中記錄的四種模式之一:

- 向最近旋轉(偶數,如果等距)

- 向負無窮大圓

- 向正無窮大圓

- 向零旋轉

您可以使用[_control87、_controlfp、_control87_2 \_ ](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C 執行時函數來修改 FPU 的舍入行為。 FPU 的預設舍入模式為"向最近旋轉」。 使用 **/QIfist**可以提高應用程式的性能,但不能沒有風險。 在依賴生產環境中使用 **/QIfist**構建的代碼之前,應徹底測試代碼對舍入模式敏感的部分。

[/arch (x86)](arch-x86.md)和 **/QIfist**不能用於同一編譯和。

> [!NOTE]
> **/QIfist**在預設情況下無效,因為舍入位也會影響浮點到浮點舍入(每次計算后發生),因此,當您為 C 樣式(向零)舍入設置標誌時,浮動點計算可能會有所不同。 如果代碼依賴於截斷浮點數的分幾部分的預期行為,則不應使用 **/QIfist。** 如果您不確定,請勿使用 **/QIfist**。

**/QIfist**選項從 Visual Studio 2005 開始被棄用。 編譯器在浮點到 int 轉換速度方面進行了顯著改進。 關於棄編譯器選項的清單,請參閱[按類別列出的編譯器選項](compiler-options-listed-by-category.md)中的**棄用與刪除編譯器選項**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 按一下 [命令列] **** 屬性頁。

1. 在 [其他選項] **** 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](q-options-low-level-operations.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
