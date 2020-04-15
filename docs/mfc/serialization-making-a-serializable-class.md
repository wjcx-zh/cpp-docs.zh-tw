---
title: 序列化：建立可序列化的類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 9648bd4f516a5f174534336b1ca3b42bb51ca0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372711"
---
# <a name="serialization-making-a-serializable-class"></a>序列化：建立可序列化的類別

製作可序列化類別需要進行五個主要步驟。 以下會列出這些步驟，並在下列各節進行說明：

1. [從 CObject(](#_core_deriving_your_class_from_cobject)`CObject`或從 派生的某些類派生)派生類。

1. [重寫序列化成員函數](#_core_overriding_the_serialize_member_function)。

1. [在類別的聲明中使用DECLARE_SERIAL宏](#_core_using_the_declare_serial_macro)。

1. [定義不採用參數的建構函數](#_core_defining_a_constructor_with_no_arguments)。

1. [在類別的實用檔案中使用IMPLEMENT_SERIAL巨集](#_core_using_the_implement_serial_macro_in_the_implementation_file)。

如果您直接調用`Serialize`,而不是通過[CArchive](../mfc/reference/carchive-class.md)的 >> 和 << 運算符調用,則序列化不需要最後三個步驟。

## <a name="deriving-your-class-from-cobject"></a><a name="_core_deriving_your_class_from_cobject"></a>從 CObject 衍生類別

基本序列化通訊協定和功能會在 `CObject` 類別中定義。 藉由從 `CObject` (或從衍生自 `CObject` 的類別) 衍生您的類別 (如下列類別 `CPerson` 的宣告)，您可以取得 `CObject` 的序列化通訊協定和功能的存取權。

## <a name="overriding-the-serialize-member-function"></a><a name="_core_overriding_the_serialize_member_function"></a>重寫序列化成員函數

`Serialize` 成員函式 (在 `CObject` 類別中定義) 會負責實際序列化擷取物件目前狀態所需的資料。 `Serialize` 函式具有一個 `CArchive` 引數，用來讀取和寫入物件資料。 [CArchive](../mfc/reference/carchive-class.md)物件具有成員函數`IsStoring`, 該函數指示`Serialize`是存儲 (寫入數據)還是載入(讀取資料)。 使用 作為`IsStoring`參考的結果,可以使用插入運算符 ()`CArchive`**<** 將物件的資料插入到物件中,或者使用提取運算符**>>**() 提取數據。

考慮派生自`CObject`並且具有兩個新成員變數的類型`CString`和**WORD**的類。 下列類別宣告片段顯示新成員變數和覆寫 `Serialize` 成員函式的宣告：

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>覆寫序列化成員函式

1. 呼叫 `Serialize` 的基底類別版本來確保已序列化物件的繼承部分。

1. 插入或擷取類別專屬的成員變數。

   插入和擷取運算子會與封存類別互動，以讀取和寫入資料。 下列範例將說明如何為先前宣告的 `Serialize` 類別實作 `CPerson`。

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

您還可以使用[CArchive::讀取](../mfc/reference/carchive-class.md#read)和[CArchive:寫入](../mfc/reference/carchive-class.md#write)成員函數來讀取和寫入大量未鍵入的數據。

## <a name="using-the-declare_serial-macro"></a><a name="_core_using_the_declare_serial_macro"></a>使用DECLARE_SERIAL宏

DECLARE_SERIAL宏在支援序列化的類聲明中是必需的,如下所示:

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

## <a name="defining-a-constructor-with-no-arguments"></a><a name="_core_defining_a_constructor_with_no_arguments"></a>定義沒有參數的建構函式

MFC 在還原序列化以重新建立您的物件時 (從磁碟載入)，需要一個預設的建構函式。 還原序列化程序需要填入所有重新建立物件所需的成員變數值。

這個建構函式可以宣告為 public、protected 或 private。 將其設定為 protected 或 private 有助於確保該函式只能由序列化函式使用。 建構函式必須讓物件處於可視需要刪除的狀態。

> [!NOTE]
> 如果忘記在使用DECLARE_SERIAL和IMPLEMENT_SERIAL宏的類中定義沒有參數的構造函數,將在使用IMPLEMENT_SERIAL宏的行上收到"無預設構造函數可用"編譯器警告。

## <a name="using-the-implement_serial-macro-in-the-implementation-file"></a><a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a>在實存檔案中使用IMPLEMENT_SERIAL巨集

IMPLEMENT_SERIAL宏用於定義從 派`CObject`生 可序列化類時所需的各種函數。 您會在實作檔 (.CPP) 中為您的類別使用這個巨集。 巨集的前兩個引數為類別的名稱及其即時基底類別的名稱。

這個巨集的第三個引數是結構描述編號。 結構描述數目基本上是類別之物件的版本號碼。 結構描述編號使用大於或等於 0 的整數 (請勿將這個結構描述編號與資料庫詞彙混淆)。

將物件讀取至記憶體時，MFC 序列化程式碼會檢查結構描述編號。 如果磁碟上物件的結構描述編號與記憶體中類別的結構描述編號不相符，程式庫會擲回 `CArchiveException`，防止您的程式讀取不正確版本的物件。

如果希望`Serialize`成員函數能夠讀取多個版本(即使用不同版本的應用程式編寫的檔),則可以使用值*VERSIONABLE_SCHEMA*作為IMPLEMENT_SERIAL宏的參數。 如需使用方式的詳細資訊和範例，請參閱類別 `GetObjectSchema` 的 `CArchive` 成員函式。

下面的範例展示如何對類別使用`CPerson`IMPLEMENT_SERIAL, 請`CObject`使用 :

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

具有可序列化類后,可以序列化類的物件,如文章[「序列化:序列化物件](../mfc/serialization-serializing-an-object.md)」中所述。

## <a name="see-also"></a>另請參閱

[序列化](../mfc/serialization-in-mfc.md)
