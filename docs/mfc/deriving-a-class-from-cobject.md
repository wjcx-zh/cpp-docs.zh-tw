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
ms.openlocfilehash: f4c01538877d8517cf3394d9e0108ce3a9df2900
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621932"
---
# <a name="deriving-a-class-from-cobject"></a>從 CObject 衍生類別

本文說明從[CObject](reference/cobject-class.md)衍生類別所需的最低步驟。 其他 `CObject` 類別文章描述利用特定功能所需的步驟 `CObject` ，例如序列化和診斷偵錯工具支援。

在討論中 `CObject` ，經常會使用「介面檔案」和「執行檔案」等詞彙。 介面檔案（通常稱為標頭檔或）。H 檔案）包含類別宣告，以及使用類別所需的任何其他資訊。 執行檔（或。CPP 檔案）包含類別定義以及用來執行類別成員函式的程式碼。 例如，針對名為的類別 `CPerson` ，您通常會建立名為 PERSON 的介面檔案。H 和名為 PERSON 的執行檔。CPP. 不過，對於某些不會在應用程式之間共用的小型類別，有時將介面和實作為結合在單一中，會比較容易。CPP 檔案。

從衍生類別時，您可以選擇四個層級的功能 `CObject` ：

- 基本功能：不支援執行時間類別資訊或序列化，但包含診斷記憶體管理。

- 基本功能加上對執行時間類別資訊的支援。

- 基本功能加上對執行時間類別資訊和動態建立的支援。

- 基本功能加上對執行時間類別資訊、動態建立和序列化的支援。

設計用來重複使用的類別（之後做為基類的類別）至少應該包含執行時間類別支援和序列化支援（如果預期會有任何未來的序列化需求）。

在宣告和實作為衍生來源的類別中，您可以使用特定宣告和執行宏來選擇功能層級 `CObject` 。

下表顯示用來支援序列化和執行時間資訊的宏之間的關聯性。

### <a name="macros-used-for-serialization-and-run-time-information"></a>用於序列化和執行時間資訊的宏

|使用的宏|CObject：： IsKindOf|CRuntimeClass：：<br /><br /> CreateObject|CArchive：： operator>><br /><br /> CArchive：： operator<<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|基本 `CObject` 功能|否|否|否|
|`DECLARE_DYNAMIC`|是|否|否|
|`DECLARE_DYNCREATE`|是|是|否|
|`DECLARE_SERIAL`|是|是|是|

#### <a name="to-use-basic-cobject-functionality"></a>使用基本 CObject 功能

1. 使用一般 c + + 語法，從 `CObject` （或從衍生自的類別）衍生您的類別 `CObject` 。

   下列範例顯示最簡單的案例，也就是衍生自的類別 `CObject` ：

   [!code-cpp[NVC_MFCCObjectSample#1](codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

不過，一般來說，您可能會想要覆寫部分的成員函式 `CObject` 來處理新類別的細節。 例如，您通常會想要覆寫的函式， `Dump` `CObject` 以提供類別內容的偵錯工具輸出。 如需如何覆寫的詳細資訊 `Dump` ，請參閱物件傾印[自訂](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))一文。 您可能也會想要覆寫的函式 `AssertValid` `CObject` ，以提供自訂的測試來驗證類別物件的資料成員是否一致。 如需如何覆寫的說明 `AssertValid` ，請參閱[MFC ASSERT_VALID 和 CObject：： AssertValid](reference/diagnostic-services.md#assert_valid)。

[指定功能層級](specifying-levels-of-functionality.md)的文章說明如何指定其他層級的功能，包括執行時間類別資訊、動態物件建立和序列化。

## <a name="see-also"></a>另請參閱

[使用 CObject](using-cobject.md)
