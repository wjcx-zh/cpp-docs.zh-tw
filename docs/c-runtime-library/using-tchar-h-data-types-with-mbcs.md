---
title: 搭配 _MBCS 使用 TCHAR.H 資料類型
description: 概述如何在使用 TCHAR 時對應 Microsoft C 執行時間文字常式。H 具有多位元組常數 _MBCS 的資料類型。
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
ms.openlocfilehash: 001f745c03e4e0c0090e40c00c5394397028659f
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589948"
---
# <a name="using-tcharh-data-types-with-_mbcs"></a>搭配 _MBCS 使用 TCHAR.H 資料類型

**Microsoft 特定的**

如泛型文字常式對應表格 (請參閱[泛型文字對應](../c-runtime-library/generic-text-mappings.md)) 所表示，當已定義資訊清單常數 **_MBCS** 時，指定的泛型文字常式會對應到下列一種常式：

- 適當地處理多位元組位元組、字元與字串的 SBCS 常式。 在此案例中，字串引數類型必須是 **char&#42;**。 例如，**_tprintf** 對應至 **printf**；**printf** 的字串引數類型為 **char&#42;**。 若為字串類型使用 **_TCHAR** 泛型文字資料類型，則 **printf** 的正式與實際參數類型會相符，因為 **_TCHAR&#42;** 對應到 **char&#42;**。

- MBCS 特定常式。 在此案例中，字串引數類型必須是 __unsigned char&#42;__。 例如， **_tcsrev** 對應至 **_mbsrev**，這預期會傳回 __unsigned char&#42;__ 類型的字串。 同樣地，如果您針對字串類型使用 **_TCHAR** 的泛型文字資料類型，就可能會發生類型衝突，因為 **_TCHAR** 對應至類型 **`char`** 。

下面是防止此類型衝突 (以及可能會產生的 C 編譯器警告或 C++ 編譯器錯誤) 的三種解決方式：

- 使用預設行為。 TCHAR.H 為執行階段程式庫中的常式提供泛型文字常式原型，如下列範例所示。

   ```C
   char *_tcsrev(char *);
   ```

   在預設案例中，**_tcsrev** 的原型透過 LIBC.LIB 中的 Thunk 對應到 **_mbsrev**。 這會將 **_mbsrev** 傳入參數與傳出結果值的類型從 **_TCHAR &#42;** (例如 **char &#42;**) 變更成 **unsigned char &#42;**。 當您使用 **_TCHAR**時，這個方法可確保類型相符，但因為函式呼叫的額外負荷，所以比較慢。

- 透過在您的程式碼中併入下列前置處理器陳述式，以內嵌方式使用函式。

   ```C
   #define _USE_INLINING
   ```

   此方法會導致在 TCHAR.H 中提供的內嵌函式 Thunk 將泛型文字常式直接對應到適當的 MBCS 常式。 從 TCHAR.H 摘錄的下列程式碼提供此程序執行方式的範例。

   ```C
   __inline char *_tcsrev(char *_s1)
   {return (char *)_mbsrev((unsigned char *)_s1);}
   ```

   若您可以使用內嵌，這是最佳解決方式，因為它可以保證類型相符，而且沒有任何額外成本。

- 透過將下列前置處理器陳述式併入您的程式碼，以使用「直接對應」。

   ```C
   #define _MB_MAP_DIRECT
   ```

   如果您不想要使用預設行為或無法使用內嵌，這種方法會提供快速替代方法。 宏會將泛型文字常式對應到常式的 MBCS 版本，如下列 TCHAR 範例所示。

   ```C
   #define _tcschr _mbschr
   ```

當您採用這種方法時，請小心確保字串引數和字串傳回值使用適當的資料類型。 您可以使用類型轉換來確保適當的類型相符，或者可以使用 **_TXCHAR** 泛型文字資料類型。 **_TXCHAR** 對應至 **`char`** SBCS 程式碼中的類型，但對應至 **`unsigned char`** MBCS 程式碼中的類型。 如需有關泛型文字巨集的詳細資訊，請參閱[泛型文字對應](../c-runtime-library/generic-text-mappings.md)。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[國際化](../c-runtime-library/internationalization.md)\
[依分類排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
