---
title: 最後一個字元在字串中的 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e207ec1d5489a629b765d398e26ac7c07771d0da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384984"
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