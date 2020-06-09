---
title: 如何：建立類型安全集合
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
ms.openlocfilehash: 6ee4603f03ef8a95c218b0fe040e9606aab99ebb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620016"
---
# <a name="how-to-make-a-type-safe-collection"></a>如何：建立類型安全集合

本文說明如何進行資料類型的類型安全集合。 主題包括：

- [使用型別安全的範本型類別](#_core_using_template.2d.based_classes_for_type_safety)

- [實作 helper 函式](#_core_implementing_helper_functions)

- [使用非範本集合類別](#_core_using_nontemplate_collection_classes)

MFC 程式庫提供以 C++ 範本為基礎的預先定義類型安全集合。 因為它們是範本，所以這些類別可在針對此目的使用非範本類別時，無需轉換類型以及額外的工作，提供類型安全和易用性。 MFC 範例[COLLECT](../overview/visual-cpp-samples.md)示範在 MFC 應用程式中使用範本型集合類別的方式。 一般而言，撰寫新的集合程式碼時都可使用這些類別。

## <a name="using-template-based-classes-for-type-safety"></a><a name="_core_using_template.2d.based_classes_for_type_safety"></a>使用型別安全的範本型類別

#### <a name="to-use-template-based-classes"></a>使用範本型類別

1. 宣告集合類別類型的變數。 例如：

   [!code-cpp[NVC_MFCCollections#7](codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. 呼叫集合物件的成員函式。 例如：

   [!code-cpp[NVC_MFCCollections#8](codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. 如有必要，請執行[helper 函數](reference/collection-class-helpers.md)和[SerializeElements](reference/collection-class-helpers.md#serializeelements)。 如需有關如何執行這些函式的詳細資訊，請參閱[執行 Helper](#_core_implementing_helper_functions)函式。

這個範例顯示整數清單的宣告。 步驟 1 中的第一個參數是儲存為清單項目的資料類型。 第二個參數指定如何在集合類別的成員函式（例如和）中傳遞和傳回資料 `Add` `GetAt` 。

## <a name="implementing-helper-functions"></a><a name="_core_implementing_helper_functions"></a>執行 Helper 函式

範本型集合類別 `CArray`、`CList` 和 `CMap` 使用五個您可以視需要為衍生的集合類別自訂的全域 helper 函式。 如需這些 helper 函式的相關資訊，請參閱*MFC 參考*中的[集合類別](reference/collection-class-helpers.md)協助程式。 對於大部分範本型集合類別的使用，需要實作序列化函式。

### <a name="serializing-elements"></a><a name="_core_serializing_elements"></a>序列化元素

`CArray`、`CList` 和 `CMap` 類別會呼叫 `SerializeElements` 將集合項目儲存至封存或從封存讀取集合項目。

`SerializeElements` helper 函式的預設實作，會根據是將物件儲存至封存還是從封存擷取物件，進行物件到封存的位元寫入，或從封存到物件的位元讀取。 如果此動作不適合，則覆寫 `SerializeElements`。

如果您的集合會儲存衍生自 `CObject` 的物件，而且您在實作集合項目類別時使用 `IMPLEMENT_SERIAL` 巨集，您可以利用內建於 `CArchive` 和 `CObject` 的序列化功能：

[!code-cpp[NVC_MFCCollections#9](codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

針對 `CArchive` `CObject::Serialize` 每個物件呼叫（或該函式的覆寫）的多載插入運算子 `CPerson` 。

## <a name="using-nontemplate-collection-classes"></a><a name="_core_using_nontemplate_collection_classes"></a>使用非樣板集合類別

MFC 也支援使用 MFC 1.0 版導入的集合類別。 這些類別不是以範本為基礎。 它們可以用來包含支援的類型、、和的資料 `CObject*` `UINT` `DWORD` `CString` 。 您可以使用這些預先定義的集合 (例如 `CObList`) 保有從 `CObject` 衍生的任何物件的集合。 MFC 也提供其他預先定義的集合來保存基本型別 `UINT` ，例如和 void 指標（ `void` *）。 不過，一般而言，定義自己的類型安全集合來保有更特定類別的物件及其系出物件，通常蠻實用的。 請注意，使用不以範本為基礎的集合類別，比使用範本型類別的工作更多。

有兩種方式可使用非範本集合建立類型安全集合：

1. 在必要時對於類型轉換使用非範本集合。 這是最簡單的方法。

1. 從非範本類型安全集合衍生並擴充。

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>對於類型轉換使用非範本集合

1. 直接使用其中一個非範本類別，例如 `CWordArray`。

   例如，您可以建立 `CWordArray` 並在其中加入任何 32 位元值，然後擷取它們。 就沒什麼要做的了。 您只要使用預先定義的功能。

   您也可以使用預先定義的集合 (例如 `CObList`) 來包含所有衍生自 `CObject` 的物件。 定義 `CObList` 集合以存放 `CObject` 的指標。 當您從清單中擷取物件時，可能必須將結果轉換為適當的類型，因為 `CObList` 函式會傳回 `CObject` 的指標。 例如，如果您在 `CPerson` 集合中儲存 `CObList` 物件，您必須將已擷取的項目轉換為 `CPerson` 物件的指標。 下列範例使用 `CObList` 集合來保有 `CPerson` 物件：

   [!code-cpp[NVC_MFCCollections#10](codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   這項技術會使用預先定義的集合類型並視需要進行轉換，可能已滿足您的許多集合的需求。 如果您需要進一步的功能或更多類型安全，請使用範本型類別或遵循下一個程序。

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>衍生並擴充非範本類型安全集合

1. 從其中一個預先定義的非範本類別，衍生您自己的集合類別。

   當您衍生您的類別時，您可以將類型安全包裝函式加入，以提供類型安全的介面給現有的函式。

   例如，如果您從 `CObList` 衍生清單以保有 `CPerson` 物件，您可以將包裝函式 `AddHeadPerson` 和 `GetHeadPerson` 加入 (如下所示)。

   [!code-cpp[NVC_MFCCollections#11](codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   這些包裝函式提供類型安全方式，從衍生的清單加入和擷取 `CPerson` 物件。 您可以為 `GetHeadPerson` 函式試試該項，您只要封裝類型轉換。

   您也可以定義擴充集合的功能而不是只包裝在類型安全包裝函式中的現有功能的新函式，來加入新的功能。 例如，[刪除 CObject 集合中的所有物件](deleting-all-objects-in-a-cobject-collection.md)一文說明了一個函式，可刪除清單中包含的所有物件。 可以將這個函式加入到衍生類別做為成員函式。

## <a name="see-also"></a>另請參閱

[集合](collections.md)
