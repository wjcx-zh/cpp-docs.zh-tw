---
title: /diagnostics （編譯器診斷選項）
ms.date: 11/11/2016
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 6b7d043e00204fa191530f03bbed069d71a25fc5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822298"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/diagnostics （編譯器診斷選項）

使用 **/diagnostics**編譯器選項來指定要顯示的錯誤和警告的位置資訊。

## <a name="syntax"></a>語法

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>備註

在 Visual Studio 2017 和更新版本支援此選項。

**/Diagnostics**編譯器選項可控制顯示的錯誤與警告資訊。

**/Diagnostics:classic**選項是預設值，它會報告僅行號，發現的問題。

**/Diagnostics:column**選項也會包含發現的問題的資料行。 這可協助您找出特定的語言建構或造成問題的字元。

**/Diagnostics:caret**選項包含的資料行，其中問題找不到，並將插入號 (^) 放置在一行程式碼在偵測到問題的位置。

請注意，在某些情況下，編譯器不會偵測的問題發生的位置。 比方說，直到其他、 未預期的符號已發生，可能無法偵測遺漏的分號。 報告資料行，並且插入號位於編譯器偵測到，是在發生問題，這不一定要請您更正的位置。

**/Diagnostics**選項是從 Visual Studio 2017 中推出。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟您的專案**屬性頁** 對話方塊。

1. 底下**組態屬性**，展開**C/c + +** 資料夾，然後選擇 **一般**屬性頁。

1. 使用中的下拉式清單控制項**診斷格式**欄位來選取診斷顯示選項。 選擇 **[確定]** 或是**套用**以儲存變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
