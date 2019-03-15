---
title: NMAKE 選項
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
ms.openlocfilehash: c60b6d821d8e16e87f86e3b79825aa1dee7867c8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824722"
---
# <a name="nmake-options"></a>NMAKE 選項

NMAKE 選項是下表中所述。 選項會加上斜線 （/） 或破折號 （-） 和不區分大小寫。 使用[！CMDSWITCHES](makefile-preprocessing-directives.md)變更 Tools.ini 或 makefile 中的選項設定。

|選項|用途|
|------------|-------------|
|/A|強制建置所有評估的目標，即使不過期，相對於相依性。 不會強制建置不相關的目標。|
|/B|即使時間戳記相等，就會建置強制。 建議只適用於非常快速的系統 （解決方式的兩秒或更少）。|
|/C|隱藏預設輸出，包括非嚴重的 NMAKE 錯誤或警告，時間戳記，以及 NMAKE 著作權訊息。 隱藏 /k 所發出的警告|
|/D|顯示評估時間戳記的每個目標和相依性和一則訊息時的目標不存在。 用於/P 與偵錯 makefile。 使用 **！CMDSWITCHES**設定或清除 /D 的 makefile 的一部分。|
|/E|會導致環境變數，以覆寫 makefile 巨集定義。|
|/ERRORREPORT[NONE &#124; PROMPT &#124; QUEUE &#124; SEND ]|如果在執行階段失敗 nmake.exe，您可以使用 /ERRORREPORT 有關這些內部錯誤，傳送給 Microsoft 的資訊。<br /><br /> 如需 /ERRORREPORT 的詳細資訊，請參閱[/errorReport （回報編譯器內部錯誤）](errorreport-report-internal-compiler-errors.md)。|
|/F *filename*|指定*filename*為 makefile。 可以在前面的空格或定位字元*filename*。 指定一次的每個 makefile /F。 若要提供從標準輸入 makefile，指定虛線 （-） *filename*，且結尾使用 f6 鍵或 CTRL + Z 的鍵盤輸入。|
|/G|顯示包含使用 ！INCLUDE 指示詞。  請參閱[Makefile 前置處理指示詞](makefile-preprocessing-directives.md)如需詳細資訊。|
|/HELP、 /？|顯示 NMAKE 命令列語法的簡短摘要。|
|/I|會忽略所有命令的結束代碼。 若要設定或清除 /I 的 makefile 的一部分，請使用 **！CMDSWITCHES**。 若要忽略的 makefile 一部分的結束代碼，使用破折號 （-） 命令修飾詞或[。忽略](dot-directives.md)。 如果同時指定，會覆寫 /K。|
|/K|如果命令傳回錯誤，會繼續建置不相關的相依性。 也會發出警告，並傳回結束代碼為 1。 根據預設，如果任何命令傳回非零結束代碼，暫止 NMAKE。 警告 /K 會隱藏由 /C;/I 會覆寫 /K，如果同時指定這兩者。|
|/N|會顯示，但不會執行命令的方式。前置處理的命令會執行。 不會顯示遞迴 NMAKE 呼叫中的命令。 適用於偵錯的 makefile，並檢查時間戳記。 若要設定或清除 /N 的 makefile 的一部分，請使用 **！CMDSWITCHES**。|
|/NOLOGO|隱藏 NMAKE 著作權訊息。|
|/P|顯示資訊 (巨集定義，推斷規則目標， [。字尾](dot-directives.md)清單) 至標準輸出，然後再執行組建。 如果不存在任何 makefile 或命令列目標，則會顯示資訊僅供參考。 您可以使用 /D 與偵錯 makefile。|
|/Q|檢查時間戳記的目標;不會執行組建。 如果任何目標不會傳回非零結束代碼如果所有目標都是最新和非零結束代碼。 前置處理的命令會執行。 從批次檔執行 NMAKE 時很有用。|
|/R|清除 **。後置詞**清單，並忽略推斷規則和 Tools.ini 檔案中所定義或預先定義的巨集。|
|/S|隱藏顯示執行的命令。 若要抑制顯示部分的 makefile，請使用**\@** 命令修飾詞或[。無訊息](dot-directives.md)。 若要設定或清除 /S 的 makefile 的一部分，請使用 **！CMDSWITCHES**。|
|/T|更新的命令列目標 （或第一個的 makefile 目標） 的時間戳記和執行前置處理命令但不會執行組建。|
|/U|必須用於搭配 /N. 傾印 inline NMAKE 檔案，以便 /N 輸出可用來當做批次檔。|
|/X *filename*|傳送至的 NMAKE 錯誤輸出*filename*而不是標準錯誤。 可以在前面的空格或定位字元*filename*。 若要將錯誤輸出傳送至標準輸出中，指定虛線 （-） *filename*。 不會影響命令標準錯誤的輸出。|
|/Y|停用批次模式推斷規則。 選取此選項時，所有的批次模式推斷規則都視為一般的推斷規則。|

## <a name="see-also"></a>另請參閱

[執行 NMAKE](running-nmake.md)
