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
ms.openlocfilehash: 368421a86d6ff6fc70455edd0ea9a32e05645007
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446359"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>透過封存儲存及載入 CObjects

透過封存儲存和載入 `CObject`，需要額外的考慮。 在某些情況下，您應該呼叫物件的 `Serialize` 函式，其中 `CArchive` 物件是 `Serialize` 呼叫的參數，而不是使用 \<的 **<>>** 或 **`CArchive`** 運算子。 要記住的重點是，`CArchive` **>>** 運算子會根據儲存檔案先前寫入檔案的 `CRuntimeClass` 資訊，在記憶體中建立 `CObject`。

因此，不論您是使用 `CArchive` **<\<** 和 **>>** 運算子，還是呼叫 `Serialize`，都取決於您是否*需要*載入封存，以根據先前儲存的 `CRuntimeClass` 資訊來動態重建物件。 在下列情況下，請使用 `Serialize` 函式：

- 還原序列化物件時，您會事先知道物件的確切類別。

- 還原序列化物件時，您已經為它配置記憶體。

> [!CAUTION]
>  如果您使用 `Serialize` 函式載入物件，您也必須使用 `Serialize` 函數來儲存物件。 請勿使用 `CArchive` **<<** 運算子來儲存，然後使用 `Serialize` 函數來載入，或使用 `Serialize` 函數來儲存，然後使用 `CArchive >>` 運算子載入。

下列範例說明案例：

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

總而言之，如果您的可序列化類別將內嵌 `CObject` 定義為成員，則*不*應該使用該物件的 `CArchive` **<\<** 和 **>>** 運算子，但應改為呼叫 `Serialize` 函數。 此外，如果您的可序列化類別定義 `CObject` 的指標（或衍生自 `CObject`的物件）做為成員，但是在自己的函式中建立此另一個物件，您也應該呼叫 `Serialize`。

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)
