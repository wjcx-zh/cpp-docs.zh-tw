---
title: no_registry 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 7c81cc2f570cb9ac4e977dac6d55cb69e491d3b2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220718"
---
# <a name="no_registry-import-attribute"></a>no_registry 匯入屬性

**no_registry**會告知編譯器不要搜尋使用`#import`匯入之類型程式庫的登錄。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***no_registry**

### <a name="parameters"></a>參數

*類型-程式庫*\
類型程式庫。

## <a name="remarks"></a>備註

如果在 include 目錄中找不到參考的類型程式庫, 即使類型程式庫位於登錄中, 編譯也會失敗。  **no_registry**會傳播至以隱含方式匯入`auto_search`的其他類型程式庫。

編譯器永遠不會在登錄中搜尋檔案名所指定的類型程式庫, 而且會直接`#import`傳遞到。

當`auto_search`指定時, 會使用`#import`初始`#import`的**no_registry**設定來產生額外的指示詞。 如果`#import` **no_registry 初始**指示詞, `#import`則產生的也會是 no_registry `auto_search`。

如果您想要匯入交叉參考的類型程式庫, **no_registry**會很有用。 它會讓編譯器不會在登錄中尋找較舊版本的檔案。 如果類型程式庫未註冊, **no_registry**也很有用。

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
