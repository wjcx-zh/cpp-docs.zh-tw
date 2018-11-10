---
title: Unicode：寬字元集
ms.date: 11/04/2016
f1_keywords:
- c.international
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 0432de1203d595947eb958a032870a929f00aeb0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618292"
---
# <a name="unicode-the-wide-character-set"></a>Unicode：寬字元集

寬字元是 2 個位元組的多語系字元碼。 在全球現代計算中使用的任何字元 (包括技術符號和特殊發行字元)，可以根據 Unicode 規格，以寬字元表示。 Unicode 標準是由包括 Microsoft 在內的數個大型組織所開發並維護，而且現在已廣為接受。

寬字元的類型是 **wchar_t**。 寬字元字串會以 **wchar_t[]** 陣列呈現，且由 `wchar_t*` 指標指向。 任何 ASCII 字元都能以寬字元呈現，方法是在該字元前附加字母 **L**。 例如，L'\0' 是結束寬 (16 位元) Null 字元。 同樣地，任何 ASCII 字串常值都能以寬字元字串常值呈現，方法是在 ASCII 常值前附加字母 L (L"Hello")。

一般而言，寬字元會比多位元組字元佔用更多的記憶體空間，但處理起來更快。 此外，在多位元組編碼中，一次只能呈現一個地區設定，而世界所有字元集都可由 Unicode 表示形式，同時呈現。

## <a name="see-also"></a>請參閱

[國際化](../c-runtime-library/internationalization.md)<br/>
[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
