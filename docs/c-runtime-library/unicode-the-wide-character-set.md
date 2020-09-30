---
title: Unicode：寬字元集
description: Microsoft C 執行時間中 Unicode 寬字元集的簡介。
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 751017a62a960eaf2afa2354a43a13971b89252a
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590156"
---
# <a name="unicode-the-wide-character-set"></a>Unicode：寬字元集

寬字元是 2 個位元組的多語系字元碼。 在全球現代計算中使用的任何字元 (包括技術符號和特殊發行字元)，可以根據 Unicode 規格，以寬字元表示。 Unicode 標準是由包括 Microsoft 在內的數個大型組織所開發並維護，而且現在已廣為接受。

寬字元的類型是 **`wchar_t`** 。 寬字元字串會以 **`wchar_t[]`** 陣列表示。 您會指向具有指標的陣列 `wchar_t*` 。 

您可以在前面加上字母，將任何 ASCII 字元表示為寬字元 `L` 。 例如， `L'\0'` 是終止的寬 (16 位) null 字元。

您可以將任何 ASCII 字串常值表示為寬字元字串常值，方法是在字母前面加上 `L` 。 例如： `L"Hello"` 。

一般而言，寬字元在記憶體中使用的空間比多位元組字元多。 但寬字元的處理速度更快。 多位元組編碼一次只能表示一個地區設定。 世界中的所有字元集都是由 Unicode 標記法同時表示。

## <a name="see-also"></a>另請參閱

[國際化](../c-runtime-library/internationalization.md)\
[依分類排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
