---
title: 序列化： 建立可序列化的類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serializable class [MFC]
- DECLARE_SERIAL macro [MFC]
- default constructor [MFC]
- VERSIONABLE_SCHEMA macro [MFC]
- classes [MFC], derived
- IMPLEMENT_SERIAL macro [MFC]
- no-arguments constructor [MFC]
- Serialize method, overriding
- defaults [MFC], constructor
- CObject class [MFC], deriving serializable classes
- constructors [MFC], defining with no arguments
- serialization [MFC], serializable classes
- no default constructor
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 378a99021ca1b48599ee934d659542384068e195
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443341"
---
# <a name="serialization-making-a-serializable-class"></a>序列化：建立可序列化的類別

製作可序列化類別需要進行五個主要步驟。 以下會列出這些步驟，並在下列各節進行說明：

1. [從 CObject 衍生您的類別](#_core_deriving_your_class_from_cobject)(或從衍生自一些類別`CObject`)。

1. [覆寫序列化成員函式](#_core_overriding_the_serialize_member_function)。

1. [使用 DECLARE_SERIAL 巨集](#_core_using_the_declare_serial_macro)類別宣告中。

1. [定義沒有引數的建構函式](#_core_defining_a_constructor_with_no_arguments)。

1. [在實作檔使用 IMPLEMENT_SERIAL 巨集](#_core_using_the_implement_serial_macro_in_the_implementation_file)為您的類別。

如果您呼叫`Serialize`直接而非透過 >> 和 << 操作員[CArchive](../mfc/reference/carchive-class.md)，最後三個步驟不需要進行序列化。

##  <a name="_core_deriving_your_class_from_cobject"></a> 從 CObject 衍生您的類別

基本序列化通訊協定和功能會在 `CObject` 類別中定義。 藉由從 `CObject` (或從衍生自 `CObject` 的類別) 衍生您的類別 (如下列類別 `CPerson` 的宣告)，您可以取得 `CObject` 的序列化通訊協定和功能的存取權。

##  <a name="_core_overriding_the_serialize_member_function"></a> 覆寫序列化成員函式

`Serialize` 成員函式 (在 `CObject` 類別中定義) 會負責實際序列化擷取物件目前狀態所需的資料。 `Serialize` 函式具有一個 `CArchive` 引數，用來讀取和寫入物件資料。 [CArchive](../mfc/reference/carchive-class.md)物件具有成員函式`IsStoring`，表示是否`Serialize`儲存 （寫入資料），或載入 （讀取資料）。 使用的結果`IsStoring`做為指南，您是插入您的物件中的資料`CArchive`物件使用插入運算子 (**<\<**) 或使用擷取運算子 (擷取資料**>>**).

請考慮衍生自類別`CObject`且具有兩個新成員變數的型別`CString`並**WORD**。 下列類別宣告片段顯示新成員變數和覆寫 `Serialize` 成員函式的宣告：

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>覆寫序列化成員函式

1. 呼叫 `Serialize` 的基底類別版本來確保已序列化物件的繼承部分。

1. 插入或擷取類別專屬的成員變數。

     插入和擷取運算子會與封存類別互動，以讀取和寫入資料。 下列範例將說明如何為先前宣告的 `Serialize` 類別實作 `CPerson`。

     [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

您也可以使用[carchive:: Read](../mfc/reference/carchive-class.md#read)並[carchive:: Write](../mfc/reference/carchive-class.md#write)成員函式來讀取和寫入大量不具類型的資料。

##  <a name="_core_using_the_declare_serial_macro"></a> 使用 DECLARE_SERIAL 巨集

DECLARE_SERIAL 巨集才會支援序列化的類別宣告中，如下所示：

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

##  <a name="_core_defining_a_constructor_with_no_arguments"></a> 定義沒有引數的建構函式

MFC 在還原序列化以重新建立您的物件時 (從磁碟載入)，需要一個預設的建構函式。 還原序列化程序需要填入所有重新建立物件所需的成員變數值。

這個建構函式可以宣告為 public、protected 或 private。 將其設定為 protected 或 private 有助於確保該函式只能由序列化函式使用。 建構函式必須讓物件處於可視需要刪除的狀態。

> [!NOTE]
>  如果您忘記使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 巨集的類別中定義不含引數的建構函式，您會收到 「 沒有預設建構函式可以使用"編譯器警告該行使用 IMPLEMENT_SERIAL 巨集的位置。

##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> 在實作檔使用 IMPLEMENT_SERIAL 巨集

IMPLEMENT_SERIAL 巨集用來定義不同的函式所需當您衍生可序列化的類別，從`CObject`。 您會在實作檔 (.CPP) 中為您的類別使用這個巨集。 巨集的前兩個引數為類別的名稱及其即時基底類別的名稱。

這個巨集的第三個引數是結構描述編號。 結構描述數目基本上是類別之物件的版本號碼。 結構描述編號使用大於或等於 0 的整數 (請勿將這個結構描述編號與資料庫詞彙混淆)。

將物件讀取至記憶體時，MFC 序列化程式碼會檢查結構描述編號。 如果磁碟上物件的結構描述編號與記憶體中類別的結構描述編號不相符，程式庫會擲回 `CArchiveException`，防止您的程式讀取不正確版本的物件。

如果您想要您`Serialize`成員函式，若要能夠讀取多個版本 — 也就是使用不同版本的應用程式所寫入的檔案 — 您可以使用值*VERSIONABLE_SCHEMA*當做 IMPLEMENT_SERIAL 的引數巨集。 如需使用方式的詳細資訊和範例，請參閱類別 `GetObjectSchema` 的 `CArchive` 成員函式。

下列範例示範如何為類別中，使用 IMPLEMENT_SERIAL `CPerson`，也就是衍生自`CObject`:

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

一旦您擁有可序列化的類別，您可以將物件序列化類別的文件中所述[序列化： 序列化物件](../mfc/serialization-serializing-an-object.md)。

## <a name="see-also"></a>另請參閱

[序列化](../mfc/serialization-in-mfc.md)

