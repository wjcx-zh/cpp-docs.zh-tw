---
title: 字串中的最後一個字元
ms.date: 11/04/2016
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
ms.openlocfilehash: 4c99628cd12738fabb877a94cfd04a4033ee45aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410666"
---
# <a name="last-character-in-a-string"></a>字串中的最後一個字元

使用下列秘訣：

- 後隨位元組範圍重疊在許多情況下設定的 ASCII 字元。 您可以安全地將任何控制字元 (小於 32) 類掃瞄來用於。

- 請考慮下列一行程式碼，它可能會檢查在字串中的最後一個字元是反斜線字元：

    ```cpp
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?
        // . . .
    ```

   因為`strlen`不是 MBCS 感知，它會傳回多位元組字串中的位元組數目，不是字元的數目。 另外，請注意，在某些字碼頁 (932，例如)，'\\' (0x5c) 是有效的後隨位元組 (`sz`是 C 字串)。

   一個可行的解決方案是這種方式重新撰寫程式碼：

    ```cpp
    char *pLast;
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )
        // . . .
    ```

   此程式碼使用 MBCS 函式`_mbsrchr`和`_mbsinc`。 因為這些函式是 MBCS 感知，他們可以區別 '\\'字元和後隨位元組'\\'。 如果字串中的最後一個字元是 null ('\0')，程式碼會執行某些動作。

## <a name="see-also"></a>另請參閱

[MBCS 程式設計提示](../text/mbcs-programming-tips.md)<br/>
[字元指派](../text/character-assignment.md)
