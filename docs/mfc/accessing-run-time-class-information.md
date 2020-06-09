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
ms.openlocfilehash: a9f90640007f84c854d59cc27e0c38459c76fe46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619191"
---
# <a name="accessing-run-time-class-information"></a>存取執行階段類別資訊

本文說明如何在執行階段存取物件之類別的資訊。

> [!NOTE]
> MFC 不會使用 Visual C++ 4.0 中引進的[執行時間類型資訊](../cpp/run-time-type-information.md)（RTTI）支援。

如果您已從[cobject](reference/cobject-class.md)衍生您的類別，並使用了**DECLARE**_**DYNAMIC**和 `IMPLEMENT_DYNAMIC` 、 `DECLARE_DYNCREATE` 和 `IMPLEMENT_DYNCREATE` ，或是 `DECLARE_SERIAL` `IMPLEMENT_SERIAL` [從 CObject 衍生類別](deriving-a-class-from-cobject.md)一文中說明的和宏，則 `CObject` 類別能夠在執行時間判斷物件的確切類別。

當需要檢查函式引數的實際類型時，以及當您必須根據物件的類別撰寫特殊用途的程式碼時，這項功能十分實用。 不過，通常不建議使用這種作法，因為這會使虛擬函式的功能重複。

`CObject` 成員函式 `IsKindOf` 可以用來判斷特定物件是否屬於指定的類別，或是否衍生自特定類別。 `IsKindOf` 的引數是一個 `CRuntimeClass` 物件，您可以使用 `RUNTIME_CLASS` 巨集透過類別的名稱來取得該物件。

### <a name="to-use-the-runtime_class-macro"></a>使用 RUNTIME_CLASS 巨集

1. 針對 `RUNTIME_CLASS` 類別使用 `CObject` 與類別名稱，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#4](codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

您很少需要直接存取執行階段類別物件。 一般用法是將執行階段類別物件傳遞至 `IsKindOf` 函式，如下一個程序所示。 `IsKindOf` 函式會測試物件是否屬於特定類別。

#### <a name="to-use-the-iskindof-function"></a>使用 IsKindOf 函式

1. 請確定類別支援執行階段類別。 也就是說，類別必須直接或間接衍生自， `CObject` 並使用宣告 _**DYNAMIC**和**DECLARE** `IMPLEMENT_DYNAMIC` 、 `DECLARE_DYNCREATE` 和 `IMPLEMENT_DYNCREATE` ，或 `DECLARE_SERIAL` `IMPLEMENT_SERIAL` [從 CObject 衍生類別一](deriving-a-class-from-cobject.md)文中說明的和宏。

1. 呼叫該類別之物件的 `IsKindOf` 成員函式，使用 `RUNTIME_CLASS` 巨集產生 `CRuntimeClass` 引數，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#2](codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  如果物件是所指定類別的成員，或衍生自指定類別的類別，則 IsKindOf 會傳回**TRUE** 。 `IsKindOf` 不支援多重繼承或虛擬基底類別，不過您可以視需要為衍生的 MFC 使用多重繼承。

執行階段類別資訊的其中一種用途是動態建立物件。 此程式會在[動態物件建立](dynamic-object-creation.md)一文中討論。

如需有關序列化和執行時間類別資訊的詳細資訊，請參閱 MFC 和[序列化](serialization-in-mfc.md)[中的檔](files-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[使用 CObject](using-cobject.md)
