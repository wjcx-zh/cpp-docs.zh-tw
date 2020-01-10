---
title: 執行 NMAKE
ms.date: 10/29/2019
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: ed56b7cd69b683caa84f184d9d72e70aac12add3
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144535"
---
# <a name="running-nmake"></a>執行 NMAKE

## <a name="syntax"></a>語法

> **NMAKE** [*選項*...][*宏*...][*目標*...][ **\@** _命令_檔 ...]

## <a name="remarks"></a>備註

NMAKE 只會建立指定的*目標*，如果未指定，則為 makefile 中的第一個目標。 第一個 makefile 目標可以是建立其他目標的[偽](description-blocks.md#pseudotargets)目標。 NMAKE 使用以 **/f**指定的 makefile，或如果未指定 **/f** ，則為目前目錄中的 makefile 檔案。 如果未指定 makefile，則會使用推斷規則來建立命令列*目標*。

*命令*檔文字檔（或回應檔）包含命令列輸入。 其他輸入可以在 \@*命令*檔前面或後面。 允許路徑。 在*命令*檔中，分行符號會被視為空格。 如果巨集定義包含空格，請將其括在引號中。

## <a name="nmake-options"></a>NMAKE 選項

下表說明 NMAKE 選項。 選項的前面會加上斜線（`/`）或破折號（`-`），不區分大小寫。 使用[`!CMDSWITCHES`](makefile-preprocessing-directives.md)來變更 Makefile 或 Tools .ini 中的選項設定。

| 選項 | 用途 |
| ------------ | ------------- |
| **/A** | 強制組建所有已評估的目標，即使不是過時的（相較于相依項）。 不會強制組建不相關的目標。 |
| **/B** | 強制組建，即使時間戳記相等也一樣。 建議僅用於快速系統（解析度2秒或更少）。 |
| **/C** | 抑制預設輸出，包括非嚴重的 NMAKE 錯誤或警告、時間戳記和 NMAKE 著作權訊息。 隱藏 **/k**所發出的警告。 |
| **/D** | 顯示每個評估目標和相依的時間戳記，以及當目標不存在時的訊息。 適用于用來對 makefile 進行偵錯工具的 **/p** 。 使用 `!CMDSWITCHES` 來設定或清除 makefile 部分的 **/d** 。 |
| **/E** | 導致環境變數覆寫 makefile 巨集定義。 |
| **/ERRORREPORT** [**無** &#124; **提示** &#124;佇列&#124; **傳送**] | 如果 nmake 在執行時間失敗，您可以使用 **/ERRORREPORT** ，將有關這些內部錯誤的資訊傳送給 Microsoft。<br /><br /> 如需詳細資訊，請參閱 [/errorReport (回報編譯器內部錯誤)](errorreport-report-internal-compiler-errors.md)。 |
| **/F** *檔案名* | 指定*filename*做為 makefile。 空格或索引標籤可以在*filename*前面。 針對每個 makefile 指定一次 **/f** 。 若要從標準輸入提供 makefile，請指定*檔案名*的虛線（`-`），並使用**F6**或**CTRL + Z**來結束鍵盤輸入。 |
| **/G** | 顯示 `!INCLUDE` 指示詞隨附的 makefile。 如需詳細資訊，請參閱[Makefile](makefile-preprocessing-directives.md)前置處理指示詞。 |
| **/Help**、 **/？** | 顯示 NMAKE 命令列語法的簡短摘要。 |
| **/I** | 忽略所有命令的結束代碼。 若要設定或清除 makefile 部分的 **/i** ，請使用 `!CMDSWITCHES`。 若要忽略 makefile 部分的結束代碼，請使用破折號（`-`）命令修飾詞或[`.IGNORE`](dot-directives.md)。 如果同時指定這兩者，則覆寫 **/k** 。 |
| **/K** | 如果命令傳回錯誤，則會繼續建立不相關的相依性。 也會發出警告，並傳回結束代碼1。 根據預設，如果有任何命令傳回非零的結束代碼，NMAKE 就會停止。 **/C**會隱藏來自 **/k**的警告; **/I**會覆寫 **/k** （如果兩者都指定）。 |
| **/N** | 會顯示但不會執行命令;執行前置處理命令。 不會在遞迴 NMAKE 呼叫中顯示命令。 適用于偵錯工具的 makefile 和檢查時間戳記。 若要設定或清除 makefile 部分的 **/n** ，請使用 `!CMDSWITCHES`。 |
| **/NOLOGO** | 抑制 NMAKE 著作權訊息。 |
| **/P** | 顯示標準輸出的資訊（巨集定義、推斷規則、目標[`.SUFFIXES`](dot-directives.md)清單），然後執行組建。 如果沒有 makefile 或命令列目標存在，則只會顯示資訊。 使用 with **/d**來進行 makefile 的調試。 |
| **一起** | 檢查目標的時間戳記;不會執行組建。 如果所有目標都是最新的，則會傳回零結束代碼，如果有任何目標已過期，則會傳回非零結束代碼。 執行前置處理命令。 從批次檔執行 NMAKE 時很有用。 |
| **/R** | 清除 `.SUFFIXES` 清單，並忽略在 Tools .ini 檔案中定義或預先定義的推斷規則和宏。 |
| **/S** | 隱藏已執行命令的顯示。 若要抑制 makefile 部分的顯示，請使用 **\@** 命令修飾詞或[`.SILENT`](dot-directives.md)。 若要設定或清除 makefile 部分的 **/s** ，請使用 `!CMDSWITCHES`。 |
| **一起** | 會更新命令列目標（或第一個 makefile 目標）的時間戳記，並執行前置處理命令，但不會執行組建。 |
| **/U** | 必須與 **/n**搭配使用。 傾印內嵌 NMAKE 檔案，讓 **/n**輸出可以當做批次檔使用。 |
| **/X** *filename* | 將 NMAKE 錯誤輸出傳送至*檔案名*，而不是標準錯誤。 空格或索引標籤可以在*filename*前面。 若要將錯誤輸出傳送至標準輸出，請指定*filename*的虛線（`-`）。 不會影響從命令到標準錯誤的輸出。 |
| **/Y** | 停用批次模式推斷規則。 選取此選項時，會將所有批次模式推斷規則視為一般推斷規則。 |

## <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE

除非使用 **/r** ，否則 NMAKE 會在讀取 makefile 之前讀取這些工具。 它會先在目前目錄中尋找 Tools .ini，然後在 INIT 環境變數所指定的目錄中。 初始化檔案中 NMAKE 設定的區段是以 `[NMAKE]` 開頭，而且可以包含任何 makefile 資訊。 在以數位記號（`#`）開頭的個別行上指定批註。

## <a name="exit-codes-from-nmake"></a>NMAKE 的結束代碼

NMAKE 會傳回下列結束代碼：

| 程式碼 | 意義 |
| ---------- | ------------- |
| 0 | 沒有錯誤（可能是警告） |
| 1 | 不完整的組建（只有在使用 **/k**時才會發出） |
| 2 | 程式錯誤，可能是由下列其中一個問題所造成：<br /> -Makefile 中的語法錯誤<br /> -命令的錯誤或結束代碼<br /> -使用者中斷 |
| 4 | 系統錯誤-記憶體不足 |
| 255 | 目標不是最新的（只有在使用 **/q**時才會發出） |

## <a name="see-also"></a>請參閱

[NMAKE 參考](nmake-reference.md)
