---
title: 使用含有 _MBCS 程式碼的 TCHAR.H 資料類型
ms.date: 11/04/2016
f1_keywords:
- tchar.h
- TCHAR
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: 62801cfc2386cf2aee7fd35a5e589d73b4f91918
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742029"
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>使用含有 _MBCS 程式碼的 TCHAR.H 資料類型

當資訊清單常數`_MBCS`是定義，指定的泛型文字常式對應至其中一個下列幾種常式：

- 適當地處理多位元組位元組、字元與字串的 SBCS 常式。 在此案例中，字串引數類型必須是 `char*`。 例如，`_tprintf` 對應到 `printf`；傳遞到 `printf` 的字串引數類型是 `char*`。 若為字串類型使用 `_TCHAR` 泛型文字資料類型，`printf` 的正式與實際參數類型會相符，因為 `_TCHAR*` 對應到 `char*`。

- MBCS 特定常式。 在此案例中，字串引數類型必須是 `unsigned char*`。 例如，`_tcsrev` 對應到 `_mbsrev`，它預期並傳回類型為 `unsigned char*` 的字串。 如果您使用`_TCHAR`泛型文字資料類型為字串類型，會潛在的類型衝突，因為`_TCHAR`對應到類型`char`。

下面是防止此類型衝突 (以及可能會產生的 C 編譯器警告或 C++ 編譯器錯誤) 的三種解決方式：

- 使用預設行為。 Tchar.h 中的執行階段程式庫，如下列範例所示的常式提供泛型文字常式原型。

    ```cpp
    char * _tcsrev(char *);
    ```

   在預設情況下，原型`_tcsrev`對應至`_mbsrev`透過 Libc.lib 中的 thunk。 這會變更的類型`_mbsrev`傳入的參數與傳出結果值從`_TCHAR*`(也就是`char *`) 來`unsigned char *`。 此方法可確保當您使用比對的型別`_TCHAR`，但會相當緩慢，因為函式呼叫額外負荷。

- 透過在您的程式碼中併入下列前置處理器陳述式，以內嵌方式使用函式。

    ```cpp
    #define _USE_INLINING
    ```

   這個方法會導致在 tchar.h 中，可將泛型文字常式直接對應到適當的 MBCS 常式中提供內嵌函式 thunk。 下列的程式碼將在 tchar.h 中摘錄示範如何做到這點。

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   若您可以使用內嵌，這是最佳解決方式，因為它可以保證類型相符，而且沒有任何額外成本。

- 使用下列前置處理器陳述式，在您的程式碼中直接對應。

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   若您不想使用預設行為或無法使用內嵌，此方法提供快速替代方式。 它會讓泛型文字常式來由巨集直接對應到常式，如來自 tchar.h 的下列範例所示的 MBCS 版本。

    ```cpp
    #define _tcschr _mbschr
    ```

   當您採用這個方法時，您必須小心以確保使用適當的資料型別字串引數和傳回值的字串。 您可以使用類型轉換來確保適當的類型相符，或者可以使用 `_TXCHAR` 泛型文字資料類型。 `_TXCHAR` 對應到類型**char**在 SBCS 程式碼，但對應到類型**unsigned char** MBCS 程式碼中。 如需有關泛型文字巨集的詳細資訊，請參閱 <<c0> [ 泛型文字對應](../c-runtime-library/generic-text-mappings.md)中*執行階段程式庫參考*。

## <a name="see-also"></a>另請參閱

[tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)
