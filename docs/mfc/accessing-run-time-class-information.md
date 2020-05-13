---
title: 存取執行階段類別資訊
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
ms.openlocfilehash: 4a836bb7bd03bd6654e5c940442fecf541042fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354218"
---
# <a name="accessing-run-time-class-information"></a>存取執行階段類別資訊

本文說明如何在執行階段存取物件之類別的資訊。

> [!NOTE]
> MFC 不使用可視化C++ 4.0 中引入[的運行時類型資訊](../cpp/run-time-type-information.md)(RTTI) 支援。

If you have derived your class from [CObject](../mfc/reference/cobject-class.md) and used `IMPLEMENT_DYNAMIC`the `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE` **DECLARE** `IMPLEMENT_SERIAL` _**DYNAMIC** and , the and , or the `DECLARE_SERIAL` and macros `CObject` explained in the article [Deriving a Class from CObject](../mfc/deriving-a-class-from-cobject.md), the class has the ability to determine the exact class of an object at run time.

當需要檢查函式引數的實際類型時，以及當您必須根據物件的類別撰寫特殊用途的程式碼時，這項功能十分實用。 不過，通常不建議使用這種作法，因為這會使虛擬函式的功能重複。

`CObject` 成員函式 `IsKindOf` 可以用來判斷特定物件是否屬於指定的類別，或是否衍生自特定類別。 `IsKindOf` 的引數是一個 `CRuntimeClass` 物件，您可以使用 `RUNTIME_CLASS` 巨集透過類別的名稱來取得該物件。

### <a name="to-use-the-runtime_class-macro"></a>使用 RUNTIME_CLASS 巨集

1. 針對 `RUNTIME_CLASS` 類別使用 `CObject` 與類別名稱，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

您很少需要直接存取執行階段類別物件。 一般用法是將執行階段類別物件傳遞至 `IsKindOf` 函式，如下一個程序所示。 `IsKindOf` 函式會測試物件是否屬於特定類別。

#### <a name="to-use-the-iskindof-function"></a>使用 IsKindOf 函式

1. 請確定類別支援執行階段類別。 That is, the class must have been derived directly `CObject` or indirectly from `IMPLEMENT_DYNAMIC`and `DECLARE_DYNCREATE` used the `DECLARE_SERIAL` `IMPLEMENT_SERIAL` **DECLARE**_**DYNAMIC** and , the and `IMPLEMENT_DYNCREATE`, or the and macros explained in the article [Deriving a Class from CObject](../mfc/deriving-a-class-from-cobject.md).

1. 呼叫該類別之物件的 `IsKindOf` 成員函式，使用 `RUNTIME_CLASS` 巨集產生 `CRuntimeClass` 引數，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  如果對像是指定類的成員或派生自指定類的類的成員,則 IsKindOf 返回**TRUE。** `IsKindOf` 不支援多重繼承或虛擬基底類別，不過您可以視需要為衍生的 MFC 使用多重繼承。

執行階段類別資訊的其中一種用途是動態建立物件。 這一過程在動態[物件創建一](../mfc/dynamic-object-creation.md)文中進行了討論。

有關序列化和運行時類資訊的更多詳細資訊,請參閱 MFC 和[序列化](../mfc/serialization-in-mfc.md)[中的文章"檔](../mfc/files-in-mfc.md)"。

## <a name="see-also"></a>另請參閱

[使用 CObject](../mfc/using-cobject.md)
