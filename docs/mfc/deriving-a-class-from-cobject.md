---
title: 從 CObject 衍生類別
ms.date: 11/04/2016
f1_keywords:
- CObject
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
ms.openlocfilehash: 26fdab5165ca098c5d7813ebf44983c261094449
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152055"
---
# <a name="deriving-a-class-from-cobject"></a>從 CObject 衍生類別

這篇文章描述衍生的類別所需的最小步驟[CObject](../mfc/reference/cobject-class.md)。 其他`CObject`類別的文章將說明利用特定所需的步驟`CObject`功能，例如序列化和診斷的偵錯支援。

在討論中旁聽的`CObject`，較常使用的詞彙 「 介面檔案 」 和 「 實作檔案 」。 介面檔案 (通常稱為標頭檔，或。H 檔案） 包含在類別宣告和使用類別時所需的任何其他資訊。 實作檔案 （或）。CPP 檔案） 包含的類別定義，以及實作類別成員函式的程式碼。 例如，對於類別，名為`CPerson`，您通常會建立名為 PERSON 介面檔案。H 與實作檔名為 PERSON。CPP。 不過，有些不會在應用程式之間共用的小型類別，可能會很結合的介面和實作到單一的工作變得更容易。CPP 檔案。

衍生的類別時，您可以選擇從四個功能層級`CObject`:

- 基本功能：不支援執行階段類別資訊或序列化，但包括診斷記憶體管理。

- 基本功能以及支援執行階段類別資訊。

- 基本功能以及支援執行階段類別資訊和動態建立。

- 基本功能以及支援執行階段類別資訊、 動態建立，以及序列化。

專為重複使用 （其會在稍後將做為基底類別） 的類別應該至少包含執行階段類別支援和序列化支援，如果預期未來序列化需要。

您選擇的功能等級使用的宣告和實作的衍生類別中特定的宣告和實作巨集`CObject`。

下表顯示用來支援序列化和執行階段資訊的巨集之間的關聯性。

### <a name="macros-used-for-serialization-and-run-time-information"></a>用於序列化和執行階段資訊的巨集

|使用的巨集|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|基本`CObject`功能|否|否|否|
|`DECLARE_DYNAMIC`|[是]|否|否|
|`DECLARE_DYNCREATE`|是|是|否|
|`DECLARE_SERIAL`|是|是|是|

#### <a name="to-use-basic-cobject-functionality"></a>使用 CObject 的基本功能

1. 使用 「 正常 」C++衍生類別中的語法`CObject`(或從衍生自`CObject`)。

   下列範例顯示簡單的情況下，類別的衍生`CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

一般來說，不過，您可能想要覆寫某些`CObject`的成員函式來處理您的新類別的詳細資訊。 例如，您通常可以覆寫`Dump`函式的`CObject`以供您類別的內容中的偵錯輸出。 如需有關如何覆寫`Dump`，請參閱文章[物件傾印自訂](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))。 您也可以覆寫`AssertValid`函式的`CObject`提供自訂的測試，以驗證資料成員的類別物件的一致性。 如需如何覆寫的說明`AssertValid`，請參閱 < [MFC ASSERT_VALID 和 CObject::AssertValid](reference/diagnostic-services.md#assert_valid)。

發行項[指定功能層級](../mfc/specifying-levels-of-functionality.md)描述如何指定其他層級的功能，包括執行階段類別資訊、 動態物件建立和序列化。

## <a name="see-also"></a>另請參閱

[使用 CObject](../mfc/using-cobject.md)
