---
title: Visual C++ 文件標記的分隔符號 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44d867f9bc33c56bf57f55d75a4f8babbbf70748
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401754"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Visual C++ 文件標記的分隔符號

使用文件標記時需要分隔符號，以向編譯器指出文件註解的開始和結束位置。

您可以搭配使用下列類型的分隔符號與 XML 文件標記︰
|||
|-|-|
|`///`  | 這是顯示在文件範例中並供 Visual C++ 專案範本使用的格式。  |
| `/** */`  | 這些是多行分隔符號。  |

使用 `/** */` 分隔符號時，有一些格式化規則：

- 對於包含 `/**` 分隔符號的行，如果該行的其餘部分是空白字元，則不會處理該行的註解。 如果第一個字元是空白字元，則會忽略該空白字元，並處理該行的其餘部分。 否則，會將 `/**` 分隔符號後面的整行文字處理為註解的一部分。

- 對於包含 `*/` 分隔符號的行，如果到 `*/` 分隔符號為止都只是空白字元，則會忽略該行。 否則，根據下列項目符號中所述的模式比對規則，會將到 `*/` 分隔符號為止的整行文字都處理為註解的一部分。

- 對於以 `/**` 分隔符號開頭之行後面的所有行，編譯器會尋找每行開頭是否有通用模式包含選擇性空白字元和星號 (`*`)，後面接著更多選擇性空白字元。 如果編譯器在每行開頭找到一組通用字元，則會忽略 `/**` 分隔符號後面所有行的模式，甚至可能到包含 `*/` 分隔符號的行。

一些範例如下：

- 下列註解中唯一會處理的部分是開頭為 `<summary>` 的那一行。 下列兩個標記格式會產生相同的註解：

    ```cpp
    /**
    <summary>text</summary>
    */
    /** <summary>text</summary> */
    ```

- 編譯器會採用 " \* " 的模式，來忽略第二行和第三行開頭。

    ```cpp
    /**
     * <summary>
     *  text </summary>*/
    ```

- 編譯器在此註解中找不到任何模式，因為第二行沒有任何星號。 因此，會將第二行和第三行 `*/` 以前的所有文字都處理為註解的一部分。

    ```cpp
    /**
     * <summary>
       text </summary>*/
    ```

- 基於兩個原因，編譯器在此註解中找不到任何模式。 首先，沒有任何一行開頭的星號前面有一致的空格數。 其次，第五行的開頭是 Tab，這與空白字元不符。 因此，會將第二行 `*/` 以前的所有文字都處理為註解的一部分。

    ```cpp
    /**
      * <summary>
      * text
     *  text2
       *  </summary>
    */
    ```

## <a name="see-also"></a>請參閱

[XML 文件](../ide/xml-documentation-visual-cpp.md)