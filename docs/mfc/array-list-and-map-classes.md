---
title: 陣列、清單和對應類別
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
ms.openlocfilehash: 9583d8263901c4a135a3ba1f560856b2a8915168
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626110"
---
# <a name="array-list-and-map-classes"></a>陣列、清單和對應類別

對於處理資料彙總，類別庫會提供集合類別群組 (陣列、清單和對應)，其可保留各種物件而預先定義的類型。 集合的大小設定可動態調整。 這些類別可用於任何程式，不論是否是為 Windows 撰寫。 但是，對於實作定義應用程式架構中文件類別的資料結構卻是最有用。 您可以從這些類別快速取得特製化的集合類別，或者可以根據範本類別建立類別。 如需這些方法的詳細資訊，請參閱文章[集合](collections.md)。 如需樣板集合類別的清單，請參閱陣列、[清單和對應的範本類別](template-classes-for-arrays-lists-and-maps.md)一文。

陣列是記憶體中連續儲存項目的一維資料結構。 陣列支援非常快速的隨機存取，因為任何特定項目的記憶體位址的計算方式是：將項目索引乘以項目大小，並將得出結果加上陣列的基底位址。 但是，如果您必須將項目插入陣列，陣列是非常耗費資源的，因為超過插入之項目的整個陣列必須移動足夠空間給要插入的項目。 陣列可以視需要放大和縮小。

清單類似陣列，但是以非常不同的方式儲存。 清單中的每個項目也包含到前一個和下一個項目的指標，使之成為雙連結清單。 因為這樣做只涉及變更幾個指標，所以可以非常快速加入或刪除項目。 不過，因為所有搜尋需要從其中一個清單結尾開始，所以搜尋清單可能會耗用相當多的資源。

對應會將索引鍵值關聯到資料值。 例如，對應的索引鍵可以是字串和指入清單的資料。 您會要求對應提供與特定字串相關聯的指標。 因為對應使用索引鍵查閱所需的雜湊資料表，所以對應搜尋時間很快速。 加入和刪除項目也很快速。 對應通常與其他資料結構搭配為輔助索引。 MFC 會使用一種特殊的對應，稱為[訊息對應](mapping-messages.md)，將視窗訊息對應至該訊息的處理常式函式的指標。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
