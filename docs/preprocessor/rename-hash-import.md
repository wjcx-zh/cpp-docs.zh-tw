---
title: 重新命名匯入屬性
ms.date: 08/29/2019
f1_keywords:
- Rename
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: ef1f64e0c268f850899efe499f7b1ad3991dd570
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216671"
---
# <a name="rename-import-attribute"></a>重新命名匯入屬性

**C++特殊**

解決名稱衝突問題。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***重新命名 (** "*OldName*" **,** "*NewName*" **)**

### <a name="parameters"></a>參數

*OldName*\
類型程式庫中的舊名稱。

*NewName*\
用來取代舊名稱的名稱。

## <a name="remarks"></a>備註

當指定**rename**屬性時, 編譯器會將*型別程式庫*中所有出現的*OldName*取代為產生的標頭檔中使用者提供的*NewName* 。

當類型程式庫中的名稱與系統標頭檔中的巨集定義相符時, 可以使用**rename**屬性。 如果未解決這種情況, 編譯器可能會發出各種語法錯誤, 例如[編譯器錯誤 C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md)和[編譯器錯誤 C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)。

> [!NOTE]
> 取代適用於類型程式庫中使用的名稱，不適用於所產生標頭檔中使用的名稱。

例如，假設屬性名稱 `MyParent` 存在於類型程式庫中，而標頭檔中已定義巨集 `GetMyParent`，且已在 `#import` 之前使用。 因為`GetMyParent`是錯誤處理`get`屬性之包裝函式的預設名稱, 所以會發生名稱衝突。 若要解決此問題，請在 `#import` 陳述式中使用下列屬性：

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

其中會重新命名類型程式庫中的名稱 `MyParent`。 嘗試重新命名 `GetMyParent` 包裝函式名稱將會失敗：

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

這是因為名稱`GetMyParent`只會出現在產生的類型程式庫標頭檔中。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
