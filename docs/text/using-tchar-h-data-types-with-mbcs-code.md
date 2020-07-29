---
title: 使用含有 _MBCS 程式碼的 TCHAR.H 資料類型
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: dd43c29d77c3351e8f597b474c4756ad3d45ef2b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215357"
---
# <a name="using-tcharh-data-types-with-_mbcs-code"></a>使用含有 _MBCS 程式碼的 TCHAR.H 資料類型

當定義了資訊清單常數時 `_MBCS` ，指定的泛型文字常式會對應到下列其中一種常式：

- 適當地處理多位元組位元組、字元與字串的 SBCS 常式。 在此情況下，字串引數應為類型 **`char*`** 。 例如， `_tprintf` 對應至 `printf` ; 的字串引數 `printf` 是類型 **`char*`** 。 如果您 `_TCHAR` 針對字串類型使用泛型文字資料類型，則會符合的正式和實際參數類型， `printf` 因為會 `_TCHAR*` 對應至 **`char*`** 。

- MBCS 特定常式。 在此案例中，字串引數類型必須是 `unsigned char*`。 例如，`_tcsrev` 對應到 `_mbsrev`，它預期並傳回類型為 `unsigned char*` 的字串。 如果您 `_TCHAR` 為字串類型使用泛型文字資料類型，可能會發生類型衝突，因為 `_TCHAR` 對應至類型 **`char`** 。

下面是防止此類型衝突 (以及可能會產生的 C 編譯器警告或 C++ 編譯器錯誤) 的三種解決方式：

- 使用預設行為。 tchar 會針對執行時間程式庫中的常式提供泛型文字常式原型，如下列範例所示。

    ```cpp
    char * _tcsrev(char *);
    ```

   在預設的情況下，的原型會 `_tcsrev` `_mbsrev` 透過 Libc 中的 Thunk 來對應。 這 `_mbsrev` 會將傳入參數和傳出傳回值的類型從 `_TCHAR*` （也就是 `char *` ）變更為 `unsigned char *` 。 當您使用時，這個方法會確保型別相符 `_TCHAR` ，但由於函式呼叫的額外負荷，因此速度相當慢。

- 透過在您的程式碼中併入下列前置處理器陳述式，以內嵌方式使用函式。

    ```cpp
    #define _USE_INLINING
    ```

   這個方法會導致 tchar 中提供的內嵌函式 Thunk，將泛型文字常式直接對應到適當的 MBCS 常式。 下列來自 tchar 的程式碼摘錄提供如何完成這項作業的範例。

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   若您可以使用內嵌，這是最佳解決方式，因為它可以保證類型相符，而且沒有任何額外成本。

- 在您的程式碼中併入下列預處理器語句，以使用直接對應。

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   若您不想使用預設行為或無法使用內嵌，此方法提供快速替代方式。 它會使一般文字常式直接由宏對應到常式的 MBCS 版本，如 tchar 中的下列範例所示。

    ```cpp
    #define _tcschr _mbschr
    ```

   當您採用這種方法時，您必須小心確保針對字串引數和字串傳回值使用適當的資料類型。 您可以使用類型轉換來確保適當的類型相符，或者可以使用 `_TXCHAR` 泛型文字資料類型。 `_TXCHAR`對應到 SBCS 程式碼中的類型， **`char`** 但會對應到 **`unsigned char`** MBCS 程式碼中的類型。 如需有關泛型文字宏的詳細資訊，請參閱《*執行時間程式庫參考*》中的[泛型文字](../c-runtime-library/generic-text-mappings.md)對應。

## <a name="see-also"></a>另請參閱

[Tchar 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)
