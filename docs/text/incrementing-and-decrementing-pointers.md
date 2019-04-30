---
title: 增量和遞減指標
ms.date: 11/04/2016
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
ms.openlocfilehash: cdaee3d13a8ceab47f62100953a0eb6e51bfc255
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410651"
---
# <a name="incrementing-and-decrementing-pointers"></a>增量和遞減指標

使用下列秘訣：

- 指向前導位元組，而非後隨位元組。 它通常是不安全的後隨位元組指標。 它通常會安全掃描轉寄而非反向的字串。

- 有指標遞增/遞減函式和巨集可以使用整個字元上移動：

    ```cpp
    sz1++;
    ```

   會變成：

    ```cpp
    sz1 = _mbsinc( sz1 );
    ```

   `_mbsinc`並`_mbsdec`函式正確遞增和遞減中`character`單位，而不用考慮字元大小。

- 遞減，您需要的標頭的字串，如下所示的指標：

    ```cpp
    sz2--;
    ```

   會變成：

    ```cpp
    sz2 = _mbsdec( sz2Head, sz2 );
    ```

   或者，您前端的指標可以指向有效的字元在字串中，以便：

    ```cpp
    sz2Head < sz2
    ```

   您必須有一個已知有效的前導位元組的指標。

- 您可能想要維護更快對前一個字元的指標`_mbsdec`。

## <a name="see-also"></a>另請參閱

[MBCS 程式設計提示](../text/mbcs-programming-tips.md)<br/>
[位元組索引](../text/byte-indices.md)
