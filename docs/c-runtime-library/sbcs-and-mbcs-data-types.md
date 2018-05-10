---
title: SBCS 和 MBCS 資料類型 | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- MBCS
- SBCS
dev_langs:
- C++
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccdec81251589ba36209f878f1fa8b727d7d2b98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS 和 MBCS 資料類型

只處理多位元組字元的一個多位元組字元或一個位元組的任何 Microsoft MBCS 執行階段程式庫常式，會預期 `unsigned int` 引數 (其中 0x00 <= 字元值 <= 0xFFFF 和 0x00 <= 位元組值 <= 0xFF )。 在字串內容中處理多位元組位元組或字元的 MBCS 常式，預期以 `unsigned char` 指標表示多位元組字元字串。

> [!CAUTION]
> 每個位元組的多位元組字元都可以 8 位元 **char** 表示。 但是值大於 0x7F 之 **char** 類型的 SBCS 或 MBCS 單一位元組字元是負數。 當這類字元直接轉換成 **int** 或 **long** 時，編譯器會延伸結果的正負號，並因此產生非預期的結果。

所以最好以 8 位元 `unsigned char` 表示一個位元組的多位元組字元。 或者，為避免負值結果，只要先將 **char** 類型的單一位元組字元轉換成 `unsigned char`，再將它轉換成 **int** 或 **long** 即可。

因為某些 SBCS 字串處理函式採用 (帶正負號的) **char\*** 參數，所以定義 **_MBCS** 時，會產生類型不符的編譯器警告。 有三種方法可以避免這個警告，位效率順序列出︰

1. 在 TCHAR.H 中使用型別安全的內嵌函式。 這是預設行為。

1. 在命令列上定義 **_MB_MAP_DIRECT**，以在 TCHAR.H 中使用直接的巨集。 如果這麼做，就必須手動對應類型。 這是最快、但類型不安全的方法。

1. 在 TCHAR.H 中使用型別安全的靜態連結程式庫函式。 若要這樣做，請在命令列上定義常數 **_NO_INLINING**。 這是最慢、但類型最安全的方法。

## <a name="see-also"></a>請參閱

[國際化](../c-runtime-library/internationalization.md)<br/>
[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
