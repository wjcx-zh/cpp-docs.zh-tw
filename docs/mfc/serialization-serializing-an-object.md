---
title: 序列化：序列化物件
ms.date: 11/04/2016
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
ms.openlocfilehash: 5c1106f180c587894283575a82a88e9e18b5c01a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290487"
---
# <a name="serialization-serializing-an-object"></a>序列化：序列化物件

發行項[序列化：建立可序列化的類別](../mfc/serialization-making-a-serializable-class.md)示範如何使類別可序列化。 一旦您擁有可序列化的類別，您可以將序列化與檔案，以透過該類別的物件[CArchive](../mfc/reference/carchive-class.md)物件。 本文說明：

- [什麼是 CArchive 物件是](../mfc/what-is-a-carchive-object.md)。

- [兩種方式可建立 CArchive](../mfc/two-ways-to-create-a-carchive-object.md)。

- [如何使用 CArchive <\<和 >> 運算子](../mfc/using-the-carchive-output-and-input-operators.md)。

- [儲存及載入 CObjects 透過封存](../mfc/storing-and-loading-cobjects-via-an-archive.md)。

您可以讓架構建立可序列化文件的封存，或明確地自行建立 `CArchive` 物件。 您也可以使用檔案和可序列化的物件之間傳輸資料 <\<和 >> 運算子`CArchive`或在某些情況下，藉由呼叫`Serialize`函式的`CObject`-衍生的類別。

## <a name="see-also"></a>另請參閱

[序列化](../mfc/serialization-in-mfc.md)
