---
title: 透過封存儲存及載入 CObjects
ms.date: 11/04/2016
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: f1b59516d5bba13b6f5e006f91d8ebd560543b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372151"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>透過封存儲存及載入 CObjects

通過存檔存儲`CObject`和載入 s 需要額外考慮。 在某些情況下,`Serialize`應呼叫物件的函數,`CArchive`其中物件是呼叫`Serialize`的參數,而不是使用**<** 的**>>** 或運算子`CArchive`。 需要記住的重要事實是,`CArchive`**>>** 運算符根據`CObject``CRuntimeClass`以前由儲存存檔寫入檔的資訊構造記憶體中。

因此,使用`CArchive`**<** 和**>>** 運算子與調用`Serialize`*取決於是否需要載入*存檔基於以前`CRuntimeClass`儲存 的資訊動態重建物件。 在以下`Serialize`使用函數:

- 當對物件進行反序列化時,您事先知道對象的確切類。

- 在反序列化物件時,已為其分配了記憶體。

> [!CAUTION]
> 如果使用函數載入物件`Serialize`,則還必須使用函`Serialize`數 儲存物件。 不要使用運算子進行儲存,`CArchive`**<<** 然後使用`Serialize`函數載入,或使用函數儲存,`Serialize`然後`CArchive >>`使用 運算符載入。

下面的範例說明了以下情況:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

`CObject`總之,如果可序列化類將嵌入定義為成員,*則不應*對該`CArchive`**<** 物件**>>** 使用和運算符,而應改為調`Serialize`用 函數。 此外,如果可序列化類別將指向(`CObject`或派生`CObject`自 ) 的物件的指標定義為成員,但在其自己的建構函數中建構此其他物件,則還應`Serialize`呼叫 。

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)
