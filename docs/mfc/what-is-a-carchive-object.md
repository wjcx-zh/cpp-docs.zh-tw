---
title: 什麼是 CArchive 物件
ms.date: 11/04/2016
f1_keywords:
- CArchive
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 08260d1a1b21658e879410ff5201e5f455535332
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519336"
---
# <a name="what-is-a-carchive-object"></a>什麼是 CArchive 物件

`CArchive` 物件針對將可序列化物件寫入 `CFile` 物件或從該物件讀取可序列化物件，提供一項類型安全緩衝機制。 通常 `CFile` 物件代表磁碟檔案，不過其可以是記憶體檔案 (`CSharedFile` 物件)，或許代表剪貼簿。

指定的 `CArchive` 物件不是要儲存 (寫入、序列化) 資料，就是要載入 (讀取、取消序列化) 資料，不過不會是兩者同時進行。 `CArchive` 物件的存留期只限於透過一次寫入物件至檔案，或從檔案讀取物件。 因此，需要兩個連續建立的 `CArchive` 物件，將資料序列化至檔案，然後從檔案將它取消序列化。

當封存檔將物件儲存至檔案時，封存檔會將 `CRuntimeClass` 名稱附加到物件。 然後，當另一個封存檔從檔案載入物件至記憶體時，`CObject` 衍生的物件會根據物件的 `CRuntimeClass` 以動態方式重建。 當指定的物件被寫入至檔案時，它可能會被參考一次以上。 載入封存檔，不過只會重建物件一次。 封存的將附加的詳細`CRuntimeClass`物件並重建物件，多個參考，並考慮可能的資訊所述[技術提示 2](../mfc/tn002-persistent-object-data-format.md)。

當資料序列化到封存時，封存會累積資料，直到緩衝區滿載。 然後，封存會將其緩衝區寫入 `CFile` 物件指向的 `CArchive` 物件。 同樣地，當您從封存讀取資料時，它會從檔案讀取資料到其緩衝區，然後從緩衝區讀取資料到您取消序列化的物件。 這個緩衝區會減少實體讀取硬碟的次數，進而提升應用程式的效能。

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)

