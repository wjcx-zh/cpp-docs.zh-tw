---
title: C 註解
ms.date: 06/25/2018
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
ms.openlocfilehash: fd2c08855bcc3ef3b4068f3841ce177d8162ff5b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152725"
---
# <a name="c-comments"></a>C 註解

「註解」是一個以正斜線和星號組合 (<strong>/\*</strong>) 為開頭的字元序列，編譯器會將其視為一個空白字元或直接忽略。 註解可以包含可表示字元集的任何字元組合，其中包括新行字元，但不包括「結尾註解」分隔符號 (<strong>\*/</strong>)。 註解可佔用一行以上，但不可以是巢狀。

註解可以出現在任何允許顯示空白字元的位置。 由於編譯器會將註解視為一個空白字元，因此您無法在語彙基元中包含註解。 編譯器會忽略註解中的字元。

使用註解來撰寫程式碼的文件。 下列範例為編譯器可接受的註解：

```C
/* Comments can contain keywords such as
   for and while without generating errors. */
```

註解可以顯示在與程式碼陳述式同一行的位置：

```C
printf( "Hello\n" );  /* Comments can go here */
```

您可以選擇在函式或程式模組之前使用描述性註解區塊：

```C
/* MATHERR.C illustrates writing an error routine
* for math functions.
*/
```

由於註解不能包含巢狀註解，下列範例會導致錯誤發生：

```C
/* Comment out this routine for testing

   /* Open file */
    fh = _open( "myfile.c", _O_RDONLY );
    .
    .
    .
*/
```

會發生錯誤是因為編譯器將 `*/` 文字後的第一個 `Open file` 辨識為註解的結尾。 當它找到註解外的 `*/` 時，會嘗試處理其餘文字並產生錯誤。

雖然您在測試時可以使用註解來呈現數行程式碼，使其無法作用，不過若要達成此目的，使用前置處理器指示詞 `#if` 和 `#endif` 和條件式編譯會更有用。 如需詳細資訊，請參閱《前置處理器參考》中的[前置處理器指示詞](../preprocessor/preprocessor-directives.md)。

**Microsoft 專屬**

Microsoft 編譯器也支援使用兩個正斜線的單行註解 (__//__)。 如果您使用 /Za 編譯 (ANSI 標準)，這些註解會產生錯誤。 這些註解不可延伸到第二行。

```C
// This is a valid comment
```

以兩個正斜線 (__//__) 做為開頭的註解，會以前方沒有逸出字元的下一個新行字元做為結束字元。 在下一個範例中，位於反斜線 (**\\**) 後方的新行字元會建立一個「逸出序列」。 此逸出序列會使編譯器將下一行視為上一行的一部分。 (如需詳細資訊，請參閱[逸出序列](../c-language/escape-sequences.md))。

```C
// my comment \
    i++;
```

因此，`i++;` 陳述式會標記為註解。

Microsoft C 預設會啟用 Microsoft 擴充功能。 使用 /Za 可停用這些擴充功能。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[C 語彙基元](../c-language/c-tokens.md)
