---
title: 執行 NMAKE
description: 瞭解如何執行 NMAKE。
ms.date: 02/09/2020
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: c2327e13e59ebf9df1ecba6fa66c6354641768ee
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743135"
---
# <a name="running-nmake"></a>執行 NMAKE

## <a name="syntax"></a>語法

> **NMAKE** [*選項*...][*宏*...][*目標*...][ **\@** _命令_檔 ...]

## <a name="remarks"></a>備註

NMAKE 只會建立指定的 *目標* ，或者，若未指定，則為 makefile 中的第一個目標。 第一個 makefile 目標可以是建立其他目標的 [偽](description-blocks.md#pseudotargets) 目標。 NMAKE 使用以 **/f**指定的 makefile，或如果未指定 **/f** ，則為目前目錄中的 makefile 檔案。 如果未指定 makefile，則會使用推斷規則來建立命令列 *目標*。

*命令*檔文字檔 (或回應檔) 包含命令列輸入。 其他輸入可以在命令檔之前或之後執行 \@ * *。 允許路徑。 在 *命令*行中，分行符號會視為空格。 如果巨集定義包含空格，請將它括在引號中。

## <a name="nmake-options"></a>NMAKE 選項

下表說明 NMAKE 選項。 選項前面會加上斜線 (`/`) 或虛線 (`-`) ，而且不區分大小寫。 使用 [`!CMDSWITCHES`](makefile-preprocessing-directives.md) 可變更 makefile 或 Tools.ini 中的選項設定。

| 選項 | 目的 |
| ------------ | ------------- |
| **/A** | 強制組建所有評估的目標，即使與相依性相比未過期也是一樣。 不會強制建立不相關目標的組建。 |
| **後退** | 即使時間戳記相等，仍會強制組建。 建議僅針對快速系統 (解析度2秒或更少的) 。 |
| **/C** | 隱藏預設輸出，包括非嚴重的 NMAKE 錯誤或警告、時間戳記和 NMAKE 著作權訊息。 隱藏由 **/k**發出的警告。 |
| **/D** | 顯示每個評估目標和相依的時間戳記，以及當目標不存在時的訊息。 對用來對 makefile 進行偵錯工具的 **/p** 很有用。 用 `!CMDSWITCHES` 來設定或清除 makefile 一部分的 **/d** 。 |
| **/E** | 導致環境變數覆寫 makefile 巨集定義。 |
| **/ERRORREPORT** [ **無** &#124; **提示** &#124; **佇列** &#124; **傳送** ] | 已取代。 [Windows 錯誤報告 (WER) ](/windows/win32/wer/windows-error-reporting) 設定控制報告。 |
| **/F** *檔案名* | 指定 *filename* 作為 makefile。 空格或索引標籤可以在 *檔案名*之前。 針對每個 makefile 指定 **/f** 一次。 若要從標準輸入提供 makefile，請 `-` 針對 *檔案名*指定破折號 () ，並以 **F6** 或 **CTRL + Z**輸入結束鍵盤輸入。 |
| **/G** | 顯示指示詞隨附的 makefile `!INCLUDE` 。 如需詳細資訊，請參閱 [Makefile](makefile-preprocessing-directives.md)前置處理指示詞。 |
| **/Help**、 **/？** | 顯示 NMAKE 命令列語法的簡短摘要。 |
| **/I** | 忽略所有命令的結束代碼。 若要針對 makefile 的一部分設定或清除 **/i** ，請使用 `!CMDSWITCHES` 。 若要忽略 makefile 一部分的結束代碼，請使用虛線 (`-`) 命令修飾詞或 [`.IGNORE`](dot-directives.md) 。 如果同時指定這兩者，則覆寫 **/k** 。 |
| **/K** | 如果命令傳回錯誤，則會繼續建立不相關的相依性。 也會發出警告，並傳回結束代碼1。 根據預設，如果有任何命令傳回非零的結束代碼，NMAKE 就會停止。 由 **/c**隱藏來自 **/k**的警告;**/I**會覆寫 **/k** （如果兩者都指定）。 |
| **N** | 顯示但不執行命令;執行前置處理命令。 不會在遞迴 NMAKE 呼叫中顯示命令。 適用于偵錯工具 makefile 和檢查時間戳記。 若要設定或清除 makefile 一部分的 **/n** ，請使用 `!CMDSWITCHES` 。 |
| **/NOLOGO** | 抑制 NMAKE 著作權訊息。 |
| **/P** | 顯示 (巨集定義、推斷規則、目標、 [`.SUFFIXES`](dot-directives.md) 列出標準輸出) 的資訊，然後執行組建。 如果沒有 makefile 或命令列目標存在，則只會顯示資訊。 使用 with **/d** 來對 makefile 進行 debug 錯。 |
| **/Q** | 檢查目標的時間戳記;不會執行組建。 如果所有目標都是最新的，則傳回零結束代碼，如果有任何目標過期，則傳回非零結束代碼。 執行前置處理命令。 從批次檔執行 NMAKE 時很有用。 |
| **/R** | 清除 `.SUFFIXES` 清單，並忽略 Tools.ini 檔案中定義或預先定義的推斷規則和宏。 |
| **/S** | 隱藏執行的命令顯示。 若要隱藏在 makefile 的一部分中顯示，請使用 **\@** 命令修飾詞或 [`.SILENT`](dot-directives.md) 。 若要針對 makefile 的一部分設定或清除 **/s** ，請使用 `!CMDSWITCHES` 。 |
| **一起** |  (或第一個 makefile 目標) 更新命令列目標的時間戳記，並執行前置處理命令，但不會執行組建。 |
| **/U** | 必須搭配 **/n**一起使用。 傾印內嵌 NMAKE 檔案，讓 **/n** 輸出可作為批次檔使用。 |
| **/X** *檔案名* | 將 NMAKE 錯誤輸出傳送至 *檔案名* ，而不是標準錯誤。 空格或索引標籤可以在 *檔案名*之前。 若要將錯誤輸出傳送至標準輸出，請 `-` 為 *檔案名*指定破折號 () 。 不會影響從命令到標準錯誤的輸出。 |
| **/Y** | 停用批次模式推斷規則。 選取此選項時，所有批次模式推斷規則都會被視為一般推斷規則。 |

## <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE

除非使用 **/r** ，否則 NMAKE 會在讀取 makefile 之前讀取 Tools.ini。 它會先在目前的目錄中尋找 Tools.ini，然後在 INIT 環境變數所指定的目錄中尋找。 初始設定檔中的 NMAKE 設定區段開頭為 `[NMAKE]` ，而且可以包含任何 makefile 資訊。 在開頭為數字元號 () 的個別行上指定批註 `#` 。

## <a name="exit-codes-from-nmake"></a>NMAKE 的結束代碼

NMAKE 會傳回下列結束代碼：

| 程式碼 | 意義 |
| ---------- | ------------- |
| 0 | 沒有錯誤 (可能是警告)  |
| 1 | 未完成的組建 (只有在使用 **/k** 時發出)  |
| 2 | 程式錯誤，可能是因為下列其中一個問題所造成：<br /> -Makefile 中的語法錯誤<br /> -來自命令的錯誤或結束代碼<br /> -使用者中斷 |
| 4 | 系統錯誤-記憶體不足 |
| 255 | 目標不是最新的 (只會在使用 **/q** 時發出)  |

## <a name="see-also"></a>另請參閱

[NMAKE 參考](nmake-reference.md)
