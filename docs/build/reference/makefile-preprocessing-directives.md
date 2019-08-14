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
ms.openlocfilehash: 4825ca180cb1b419a9ffa5232575ba1a24f8805d
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980517"
---
# <a name="makefile-preprocessing-directives"></a>Makefile 前置處理指示詞

前置處理指示詞不會區分大小寫。 初始驚嘆號 (!) 必須出現在行首。 驚嘆號之後可以出現零或多個空格或索引標籤, 以進行縮排。

- `!CMDSWITCHES`{`+` &#124; } 選項 ... `-`

   開啟或關閉每個*選項*。 空格或索引標籤必須出現`+`在`-` or 運算子之前; 運算子和[選項字母](running-nmake.md#nmake-options)之間不能出現任何值。 字母不會區分大小寫, 且指定時不會`/`有斜線 ()。 若要開啟一些選項並關閉其他選項, 請使用的`!CMDSWITCHES`個別規格。

   只有/D、/I、/N 和/S 可以用於 makefile。 在 Tools .ini 中, 除了/F、/HELP、/NOLOGO、/X 和/？以外, 允許所有選項。 在描述區塊中指定的變更在下一個描述區塊之前不會生效。 這個指示詞會更新**MAKEFLAGS**;如果指定**MAKEFLAGS** , 則遞迴期間會繼承變更。

- `!ERROR`*文字*

   會在錯誤 U1050 中顯示*文字*, 然後中止 NMAKE, 即使使用/k、 `.IGNORE`/i `!CMDSWITCHES`、、或虛線 (`-`) 命令修飾詞也一樣。 *文字*前面的空格或定位字元會被忽略。

- `!MESSAGE`*文字*

   將*文字*顯示為標準輸出。 *文字*前面的空格或定位字元會被忽略。

- `!INCLUDE`[ `<` ] *filename* [ `>` ]

   將*filename*讀取為 makefile, 然後繼續進行目前的 makefile。 NMAKE 會先在指定的或目前的目錄中搜尋*filename* , 然後以遞迴方式在任何父系 makefile 的目錄中搜尋, 然後, 如果*filename*是`< >`以角括弧 () 括住, 則會在所指定的**目錄中。包含**宏, 這一開始會設定為 INCLUDE 環境變數。 將設定、 `.SUFFIXES` `.PRECIOUS`和推斷規則傳遞至遞迴 makefile 很有用。

- `!IF`*constant_expression*

   在`!IF`和下一個`!ELSE` , 或`!ENDIF`如果*constant_expression*評估為非零值時, 處理語句。

- `!IFDEF`*macroname*

   如果已定義`!IFDEF` *macroname* , 則`!ELSE`會`!ENDIF`在和下一個或之間處理語句。 會將 null 宏視為已定義。

- `!IFNDEF`*macroname*

   如果未定義`!IFNDEF` *macroname* , 則`!ELSE`會`!ENDIF`在和下一個或之間處理語句。

- `!ELSE`[`IF` &#124; *constant_expression* &#124; *macroname* macroname] `IFDEF` `IFNDEF`

   `!ELSE`如果先前的、`!IFNDEF`或語句`!ENDIF`評估為零, `!IFDEF`則在和下一個中處理語句。 `!IF` 選擇性關鍵字會進一步控制前置處理。

- `!ELSEIF`

   並為 `!ELSE IF` 的同義字。

- `!ELSEIFDEF`

   並為 `!ELSE IFDEF` 的同義字。

- `!ELSEIFNDEF`

   並為 `!ELSE IFNDEF` 的同義字。

- `!ENDIF`

   標記`!IF`、 `!IFDEF`或區塊的結尾。`!IFNDEF` 在同一行`!ENDIF`之後的任何文字都會被忽略。

- `!UNDEF`*macroname*

   取消*macroname*。

## <a name="see-also"></a>另請參閱

- [Makefile 前置處理](makefile-preprocessing.md)