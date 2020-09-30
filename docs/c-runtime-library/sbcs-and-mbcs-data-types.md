---
title: SBCS 和 MBCS 資料類型
description: 如何在 Microsoft C 執行時間中表示單一和多位元組字元。
ms.topic: conceptual
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 27d32ffd079cdc82ab8a799df9d9ec778b546a3b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590247"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS 和 MBCS 資料類型

任何只處理1位元組字元或1位元組多位元組字元的 Microsoft MBCS 執行時間程式庫常式，都需要 **`unsigned int`** 引數 (其中 0x00 <= 字元值 <= 0xffff 和 0x00 <= 位元組值 <= 0xff) 。 在字串內容中處理多位元組位元組或字元的 MBCS 常式，需要以多位元組字元字串表示為 **`unsigned char`** 指標。

> [!CAUTION]
> 多位元組字元的每個位元組都可以用8位表示 **`char`** 。 但是，值大於0x7F 之類型的 SBCS 或 MBCS 單一位元組字元 **`char`** 是負數。 當這類字元直接轉換成或時 **`int`** **`long`** ，結果會由編譯器進行簽署，因此可能會產生非預期的結果。

最好將多位元組字元的位元組表示為8位 **`unsigned char`** 。 或者，若要避免負的結果，請先將類型的單一位元組字元轉換成， **`char`** **`unsigned char`** 再將它轉換成 **`int`** 或 **`long`** 。

因為某些 SBCS 字串處理函式採用 (簽署的) **`char`** <strong>\*</strong> 參數，所以在定義 **_MBCS**時，將會產生類型不符的編譯器警告。 有三種方法可以避免這個警告，位效率順序列出︰

1. 在 TCHAR.H 中使用型別安全的內嵌函式。 這是預設行為。

1. 在命令列上定義 **_MB_MAP_DIRECT**，以在 TCHAR.H 中使用直接的巨集。 如果這麼做，就必須手動對應類型。 這是最快速的方法，但不是型別安全。

1. 在 TCHAR.H 中使用型別安全的靜態連結程式庫函式。 若要這樣做，請在命令列上定義常數 **_NO_INLINING**。 這是最慢、但類型最安全的方法。

## <a name="see-also"></a>另請參閱

[國際化](../c-runtime-library/internationalization.md)<br/>
[依分類排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
