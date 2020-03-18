---
title: 從 CObject 衍生類別
ms.date: 11/04/2016
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
ms.openlocfilehash: 860af88512acb33ff3035b3a04609165953d80a8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446973"
---
# <a name="deriving-a-class-from-cobject"></a>從 CObject 衍生類別

本文說明從[CObject](../mfc/reference/cobject-class.md)衍生類別所需的最低步驟。 其他 `CObject` 類別文章描述利用特定 `CObject` 功能所需的步驟，例如序列化和診斷偵錯工具支援。

在 `CObject`的討論中，經常會使用「介面檔案」和「執行檔案」等詞彙。 介面檔案（通常稱為標頭檔或）。H 檔案）包含類別宣告，以及使用類別所需的任何其他資訊。 執行檔（或。CPP 檔案）包含類別定義以及用來執行類別成員函式的程式碼。 例如，針對名為 `CPerson`的類別，您通常會建立名為 PERSON 的介面檔案。H 和名為 PERSON 的執行檔。CPP. 不過，對於某些不會在應用程式之間共用的小型類別，有時將介面和實作為結合在單一中，會比較容易。CPP 檔案。

從 `CObject`衍生類別時，您可以選擇四個層級的功能：

- 基本功能：不支援執行時間類別資訊或序列化，但包含診斷記憶體管理。

- 基本功能加上對執行時間類別資訊的支援。

- 基本功能加上對執行時間類別資訊和動態建立的支援。

- 基本功能加上對執行時間類別資訊、動態建立和序列化的支援。

設計用來重複使用的類別（之後做為基類的類別）至少應該包含執行時間類別支援和序列化支援（如果預期會有任何未來的序列化需求）。

您可以使用宣告和實作為衍生自 `CObject`的類別，來選擇功能層級。

下表顯示用來支援序列化和執行時間資訊的宏之間的關聯性。

### <a name="macros-used-for-serialization-and-run-time-information"></a>用於序列化和執行時間資訊的宏

|使用的宏|CObject：： IsKindOf|CRuntimeClass：：<br /><br /> CreateObject|CArchive：： operator > ><br /><br /> CArchive：： operator < <|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|基本 `CObject` 功能|否|否|否|
|`DECLARE_DYNAMIC`|是|否|否|
|`DECLARE_DYNCREATE`|是|是|否|
|`DECLARE_SERIAL`|是|是|是|

#### <a name="to-use-basic-cobject-functionality"></a>使用基本 CObject 功能

1. 使用一般C++語法，從 `CObject` （或從 `CObject`衍生的類別）衍生您的類別。

   下列範例顯示最簡單的案例，也就是從 `CObject`的類別衍生：

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

不過，一般來說，您可能會想要覆寫部分 `CObject`的成員函式，以處理新類別的細節。 例如，您通常會想要覆寫 `CObject` 的 `Dump` 功能，以提供類別內容的偵錯工具輸出。 如需如何覆寫 `Dump`的詳細資訊，請參閱物件傾印[自訂](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))一文。 您可能也會想要覆寫 `CObject` 的 `AssertValid` 函式，以提供自訂的測試來驗證類別物件的資料成員是否一致。 如需如何覆寫 `AssertValid`的說明，請參閱[MFC ASSERT_VALID 和 CObject：： AssertValid](reference/diagnostic-services.md#assert_valid)。

[指定功能層級](../mfc/specifying-levels-of-functionality.md)的文章說明如何指定其他層級的功能，包括執行時間類別資訊、動態物件建立和序列化。

## <a name="see-also"></a>另請參閱

[使用 CObject](../mfc/using-cobject.md)
