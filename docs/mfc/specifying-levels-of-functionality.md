---
title: 指定功能層級
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
ms.openlocfilehash: 3fb9b18712b24046e05f05834caaac2819fb73dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494649"
---
# <a name="specifying-levels-of-functionality"></a>指定功能層級

這篇文章說明如何加入下列的層級的功能，您[CObject](../mfc/reference/cobject-class.md)-衍生的類別：

- [執行階段類別資訊](#_core_to_add_run.2d.time_class_information)

- [動態建立支援](#_core_to_add_dynamic_creation_support)

- [序列化支援](#_core_to_add_serialization_support)

如需一般的描述`CObject`功能，請參閱文章[從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md)。

- [執行階段類別資訊](#_core_to_add_run.2d.time_class_information)
#### <a name="_core_to_add_run.2d.time_class_information"></a> 若要新增執行階段類別資訊

1. 衍生您的類別，從`CObject`中所述[從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md)文章。

1. 在類別宣告中，使用 DECLARE_DYNAMIC 巨集，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]

1. 使用 IMPLEMENT_DYNAMIC 巨集在實作檔 (。CPP) 您的類別。 這個巨集接受做為引數類別和其基底類別的名稱，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]

> [!NOTE]
>  一律將您的類別放在實作檔 (。CPP) 為您的類別。 IMPLEMENT_DYNAMIC 巨集應該只評估一次在編譯期間，因此應該不用於介面檔案中 (。H），可能無法包含在多個檔案。

#### <a name="_core_to_add_dynamic_creation_support"></a> 若要加入動態建立支援

1. 衍生您的類別，從`CObject`。

1. 在類別宣告中使用 DECLARE_DYNCREATE 巨集。

1. 定義沒有引數 （預設建構函式） 的建構函式。

1. 在類別實作檔使用 IMPLEMENT_DYNCREATE 巨集。

#### <a name="_core_to_add_serialization_support"></a> 若要加入的序列化支援

1. 衍生您的類別，從`CObject`。

1. 覆寫`Serialize`成員函式。

    > [!NOTE]
    >  如果您呼叫`Serialize`直接，也就是不想將序列化物件，可透過多型的指標，並略過步驟 3 到 5。

1. 在類別宣告中使用 DECLARE_SERIAL 巨集。

1. 定義沒有引數 （預設建構函式） 的建構函式。

1. 在類別實作檔使用 IMPLEMENT_SERIAL 巨集。

> [!NOTE]
>  「 多型的指標 」 指向類別的物件 (呼叫它的) 或衍生自 （例如，B） 任何類別的物件。 若要序列化透過多型的指標，framework 必須判斷執行階段類別，因為它可能是衍生自基底類別 (A) 任何類別的物件序列化 (B) 的物件。

如需如何啟用序列化，當您衍生您的類別，從詳細`CObject`，請參閱文章[MFC 中的檔案](../mfc/files-in-mfc.md)並[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md)
