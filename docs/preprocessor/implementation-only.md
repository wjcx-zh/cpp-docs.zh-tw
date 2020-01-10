---
title: implementation_only 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: 08144b3c815350acfe6a856b36d2d88085d1c04d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218982"
---
# <a name="implementation_only-import-attribute"></a>implementation_only 匯入屬性

**C++特殊**

抑制`.tlh`主要型別程式庫標頭檔的產生。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***implementation_only**

## <a name="remarks"></a>備註

這個檔案包含所有用於公開類型程式庫內容的宣告。 `.tli`標頭檔會產生包裝函式成員函式的執行, 並包含在編譯中。

當指定這個屬性時, `.tli`標頭的內容會與一般用於`.tlh`標頭的命名空間相同。 此外，不會將成員函式宣告為內嵌。

**Implementation_only**屬性適用于搭配[no_implementation](../preprocessor/no-implementation.md)屬性使用, 做為將執行程式從先行編譯標頭檔 (PCH) 中排除的方式。 具有 `#import` 屬性的 `no_implementation` 陳述式是置於用來建立 PCH 的來源範圍中。 產生的 PCH 會供許多原始程式檔使用。 然後, 具有**implementation_only**屬性的語句會在PCH區域外使用。`#import` 您只需要在其中一個原始檔中使用此語句一次。 它會產生所有必要的包裝函式成員函式, 而不需重新編譯每個原始程式檔。

> [!NOTE]
> `#import` `no_implementation`一個 `#import`語句中的 implementation_only 屬性必須與另一個語句 (屬於相同類型程式庫) 搭配屬性一起使用。 否則, 就會產生編譯器錯誤。 這是因為`#import` `no_implementation`具有屬性的語句所產生的包裝函式類別定義, 必須用來編譯**implementation_only**屬性所產生的實現。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
