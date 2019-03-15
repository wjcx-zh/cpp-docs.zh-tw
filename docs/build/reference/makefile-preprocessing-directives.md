---
title: Makefile 前置處理指示詞
ms.date: 06/14/2018
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 0945d0e1c149b7e1ab31b0dbbd5003f8b15a1e4d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824819"
---
# <a name="makefile-preprocessing-directives"></a>Makefile 前置處理指示詞

前置處理器指示詞不區分大小寫。 初始驚嘆號 （！） 必須出現在一行的開頭。 零或多個空間索引標籤可以顯示驚嘆號的 縮排後。

- **!CMDSWITCHES** {**+** &#124; **-**}*option* ...

   開啟每個*選項*列出開啟或關閉。 空格或定位字元必須出現在之前 + 或-運算子;都不出現 between 運算子和[選項字母](nmake-options.md)。 字母不區分大小寫，且會指定不含斜線 （/）。 若要開啟上的一些選項並關閉其他選項，可分別指定 **！CMDSWITCHES**。

   只有 /D / 我、 /N 和 /S 可用 makefile 中。 除了 /F、 /HELP、 /NOLOGO，允許 Tools.ini，所有的選項/X，，/？。 描述區塊中指定的變更才會生效之前的下一個描述區塊。 這個指示詞會更新**MAKEFLAGS**; 如果在遞迴期間會繼承變更**MAKEFLAGS**指定。

- **!ERROR**  *text*

   顯示*文字*錯誤 U1050，則會中止 NMAKE，即使在 /K，/ 我， **。略過**， **！CMDSWITCHES**，或使用破折號 （-） 命令修飾詞。 空間或標籤之前*文字*都會被忽略。

- **!MESSAGE**  *text*

   顯示*文字*至標準輸出。 空間或標籤之前*文字*都會被忽略。

- **!INCLUDE** [ **\<** ] *filename* [ **>** ]

   讀取*filename*為 makefile，再繼續執行目前的 makefile。 搜尋 NMAKE*檔名*第一次在指定或目前的目錄中，然後遞迴地目錄的任何父系的 makefile，然後，如果*filename*加上角括弧 (\<>)，在所指定的目錄**INCLUDE**巨集，一開始是設定為 INCLUDE 環境變數。 可用來傳遞 **。尾碼**設定， **。寶貴**，與推斷規則，以遞迴的 makefile。

- **!IF** *constant_expression*

   處理陳述式之間 **！如果**和 [下一步] **！ELSE**或 **！ENDIF**如果*constant_expression*評估為非零值。

- **!IFDEF**  *macroname*

   處理陳述式之間 **！IFDEF**和 [下一步] **！ELSE**或 **！ENDIF**如果*macroname*定義。 Null 巨集視為定義。

- **!IFNDEF**  *macroname*

   處理陳述式之間 **！IFNDEF**和 [下一步] **！ELSE**或 **！ENDIF**如果*macroname*未定義。

- **!ELSE** [**IF** *constant_expression* &#124; **IFDEF** *macroname* &#124; **IFNDEF** *macroname*]

   處理陳述式之間 **！ELSE**和 [下一步] **！ENDIF**如果之前 **！如果**， **！IFDEF**，或 **！IFNDEF**陳述式評估為零。 選擇性關鍵字提供進一步的前置處理的控制項。

- **!ELSEIF**

   同義字 **！ELSE IF**。

- **!ELSEIFDEF**

   同義字 **！其他 IFDEF**。

- **!ELSEIFNDEF**

   同義字 **！其他 IFNDEF**。

- **!ENDIF**

   標記的結尾 **！如果**， **！IFDEF**，或 **！IFNDEF**區塊。 之後的任何文字 **！ENDIF**同一行上會被忽略。

- **!UNDEF**  *macroname*

   取消定義*macroname*。

## <a name="see-also"></a>另請參閱

- [Makefile 前置處理](makefile-preprocessing.md)