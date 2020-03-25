---
title: Makefile 前置處理指示詞
ms.date: 08/11/2019
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
ms.openlocfilehash: 1dd30c8e338343626d8a8cc3157d118e44f0ea18
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170484"
---
# <a name="makefile-preprocessing-directives"></a>Makefile 前置處理指示詞

前置處理指示詞不會區分大小寫。 初始驚嘆號（！）必須出現在行首。 驚嘆號之後可以出現零或多個空格或索引標籤，以進行縮排。

- `!CMDSWITCHES` {`+` &#124; `-`}*選項*。

   開啟或關閉每個*選項*。 空格或索引標籤必須出現在 `+` 或 `-` 運算子之前;運算子和[選項字母](running-nmake.md#nmake-options)之間不能出現任何。 字母不會區分大小寫，且指定時不會有斜線（`/`）。 若要開啟一些選項並關閉其他選項，請使用 `!CMDSWITCHES`的個別規格。

   只有/D、/I、/N 和/S 可以用於 makefile。 在 Tools .ini 中，除了/F、/HELP、/NOLOGO、/X 和/？以外，允許所有選項。 在描述區塊中指定的變更在下一個描述區塊之前不會生效。 這個指示詞會更新**MAKEFLAGS**;如果指定**MAKEFLAGS** ，則遞迴期間會繼承變更。

- `!ERROR`*文字*

   會在錯誤 U1050 中顯示*文字*，然後中止 NMAKE，即使使用/K、/i、`.IGNORE`、`!CMDSWITCHES`或破折號（`-`）命令修飾詞也一樣。 *文字*前面的空格或定位字元會被忽略。

- `!MESSAGE`*文字*

   將*文字*顯示為標準輸出。 *文字*前面的空格或定位字元會被忽略。

- `!INCLUDE` [`<`]*檔案名*[`>`]

   將*filename*讀取為 makefile，然後繼續進行目前的 makefile。 NMAKE 會先在指定的或目前的目錄中搜尋*filename* ，然後以遞迴方式在任何父系 makefile 的目錄中搜尋，然後，如果*filename*以角括弧（`< >`）括住，則會在**包含**宏指定的目錄中（一開始設定為 include 環境變數）。 將 `.SUFFIXES` 設定、`.PRECIOUS`和推斷規則傳遞至遞迴 makefile 很有用。

- `!IF` *constant_expression*

   如果*constant_expression*評估為非零值，則會在 `!IF` 和下一個 `!ELSE` 或 `!ENDIF` 之間處理語句。

- `!IFDEF` *macroname*

   在 `!IFDEF` 和下一個 `!ELSE` 之間處理語句，如果已定義*macroname* ，則為 `!ENDIF`。 會將 null 宏視為已定義。

- `!IFNDEF` *macroname*

   在 `!IFNDEF` 和下一個 `!ELSE` 之間處理語句，如果未定義*macroname* ，則為 `!ENDIF`。

- `!ELSE` [`IF` *constant_expression* &#124; `IFDEF` *macroname* &#124; `IFNDEF` *macroname*]

   如果先前的 `!IF`、`!IFDEF`或 `!IFNDEF` 語句評估為零，則會在 `!ELSE` 和下一個 `!ENDIF` 之間處理語句。 選擇性關鍵字會進一步控制前置處理。

- `!ELSEIF`

   並為 `!ELSE IF` 的同義字。

- `!ELSEIFDEF`

   並為 `!ELSE IFDEF` 的同義字。

- `!ELSEIFNDEF`

   並為 `!ELSE IFNDEF` 的同義字。

- `!ENDIF`

   標記 `!IF`、`!IFDEF`或 `!IFNDEF` 區塊的結尾。 在同一行 `!ENDIF` 之後的任何文字都會被忽略。

- `!UNDEF` *macroname*

   取消*macroname*。

## <a name="see-also"></a>另請參閱

- [Makefile 前置處理](makefile-preprocessing.md)
