---
title: SBCS 和 MBCS 資料類型
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 72215b7a3fff638daf02f136e3a107ce8a8a00d5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233908"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS 和 MBCS 資料類型

任何只處理多位元組字元之一個多位元組字元或一個位元組的 Microsoft MBCS 執行時間程式庫常式，都需要一個 **`unsigned int`** 引數（其中 0x00 <= 字元值 <= 0xffff，而 0x00 <= byte 值 <= 0xff）。 在字串內容中處理多位元組位元組或字元的 MBCS 常式，需要以多位元組字元字串表示為 **`unsigned char`** 指標。

> [!CAUTION]
> 多位元組字元的每個位元組都可以用8位表示 **`char`** 。 不過，值大於0x7F 之類型的 SBCS 或 MBCS 單一位元組字元 **`char`** 是負數。 當這類字元直接轉換成或時 **`int`** **`long`** ，編譯器會對其進行正負號延伸，因此會產生非預期的結果。

因此，最好將多位元組字元的位元組表示為8位 **`unsigned char`** 。 或者，若要避免負面結果，只需將類型的單一位元組字元轉換成， **`char`** **`unsigned char`** 再將它轉換成 **`int`** 或 **`long`** 。

因為某些 SBCS 字串處理函式採用（帶正負號） **`char`** <strong>\*</strong> 參數，所以在定義 **_MBCS**時，將會產生類型不符的編譯器警告。 有三種方法可以避免這個警告，位效率順序列出︰

1. 在 TCHAR.H 中使用型別安全的內嵌函式。 此為預設行為。

1. 在命令列上定義 **_MB_MAP_DIRECT**，以在 TCHAR.H 中使用直接的巨集。 如果這麼做，就必須手動對應類型。 這是最快、但類型不安全的方法。

1. 在 TCHAR.H 中使用型別安全的靜態連結程式庫函式。 若要這樣做，請在命令列上定義常數 **_NO_INLINING**。 這是最慢、但類型最安全的方法。

## <a name="see-also"></a>另請參閱

[國際化](../c-runtime-library/internationalization.md)<br/>
[依分類排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
