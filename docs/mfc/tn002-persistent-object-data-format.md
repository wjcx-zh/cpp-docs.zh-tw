---
title: TN002：持續性物件資料格式
ms.date: 11/04/2016
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 1880d5d43055966dea8ab16dc4f26bd4e4602ec5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447135"
---
# <a name="tn002-persistent-object-data-format"></a>TN002：持續性物件資料格式

此附注描述支援持續C++性物件的 MFC 常式，以及儲存在檔案中的物件資料格式。 這只適用于具有[DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)宏的類別。

## <a name="the-problem"></a>問題

持續性資料的 MFC 執行會將許多物件的資料儲存在檔案的單一連續部分。 物件的 `Serialize` 方法會將物件的資料轉譯成壓縮二進位格式。

此實作為保證所有資料都是使用[CArchive 類別](../mfc/reference/carchive-class.md)，以相同的格式儲存。 它會使用 `CArchive` 物件做為翻譯工具。 在您呼叫[CArchive：： Close](../mfc/reference/carchive-class.md#close)之前，此物件會從其建立的時間繼續進行。 此方法可由程式設計人員明確地呼叫，或在程式結束包含 `CArchive`的範圍時由析構函式隱含呼叫。

此附注描述 `CArchive` 成員[CArchive：： ReadObject](../mfc/reference/carchive-class.md#readobject)和[CArchive：： WriteObject](../mfc/reference/carchive-class.md#writeobject)的執行。 您會在 Arcobj 中找到這些函式的程式碼，以及在 Arccore 中 `CArchive` 的主要執行。 使用者程式碼不會直接呼叫 `ReadObject` 和 `WriteObject`。 相反地，這些物件是由 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏自動產生的類別特定型別安全插入和抽取運算子所使用。 下列程式碼顯示如何隱含地呼叫 `WriteObject` 和 `ReadObject`：

```
class CMyObject : public CObject
{
    DECLARE_SERIAL(CMyObject)
};

IMPLEMENT_SERIAL(CMyObj, CObject, 1)

// example usage (ar is a CArchive&)
CMyObject* pObj;
CArchive& ar;
ar <<pObj;        // calls ar.WriteObject(pObj)
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))
```

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>將物件儲存到存放區（CArchive：： WriteObject）

方法 `CArchive::WriteObject` 會寫入用來重建物件的標頭資料。 這項資料是由兩個部分所組成：物件的類型和物件的狀態。 這個方法也會負責維護所寫出之物件的識別，因此不論該物件的指標數目（包括迴圈指標）為何，只會儲存一個複本。

儲存（插入）和還原（解壓縮）物件需依賴數個「資訊清單常數」。 這些是以二進位儲存的值，並提供重要的資訊給封存（請注意，"w" 前置詞表示16位的數量）：

|Tag|描述|
|---------|-----------------|
|wNullTag|用於 Null 物件指標（0）。|
|wNewClassTag|表示此封存內容（-1）的新下面的類別描述。|
|wOldClassTag|表示在此內容（0x8000）中看到正在讀取之物件的類別。|

儲存物件時，封存會維護一個[CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) （ *m_pStoreMap*），這是從預存物件到32位持續性識別碼（PID）的對應。 PID 會指派給每個唯一的物件，以及儲存在封存內容中的每個唯一類別名稱。 這些 Pid 會依序從1開始。 這些 Pid 在封存範圍外沒有任何重要性，特別是不會與記錄號碼或其他身分識別專案混淆。

在 `CArchive` 類別中，Pid 是32位，但它們會寫成16位，除非它們大於0x7FFE。 大型 Pid 會寫成0x7FFF，後面接著32位 PID。 這會維持與舊版中所建立之專案的相容性。

當提出要求將物件儲存至封存（通常是使用全域插入運算子）時，會檢查 Null [CObject](../mfc/reference/cobject-class.md)指標。 如果指標是 Null，則會將*wNullTag*插入封存資料流程中。

如果指標不是 Null，而且可以序列化（類別是 `DECLARE_SERIAL` 類別），則程式碼會檢查*m_pStoreMap*以查看是否已儲存物件。 如果有，程式碼就會將與該物件相關聯的32位 PID 插入封存資料流程中。

如果之前尚未儲存物件，有兩種可能的考慮：物件和物件的確切型別（也就是類別）都是這個封存內容的新手，或者物件是已經看過的確切型別。 為了判斷是否已看到該類型，程式碼會查詢*m_pStoreMap* ，找出符合與所儲存物件相關聯之 `CRuntimeClass` 物件的[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)物件。 如果有相符的結果，`WriteObject` 會插入一個標記，這是*wOldClassTag*和此索引的位 `OR`。 如果 `CRuntimeClass` 是此封存內容的新手，`WriteObject` 會將新的 PID 指派給該類別，並將其插入封存中，並在前面加上*wNewClassTag*值。

然後，使用 `CRuntimeClass::Store` 方法，將此類別的描述項插入封存中。 `CRuntimeClass::Store` 插入類別的架構編號（請參閱下文）和類別的 ASCII 文字名稱。 請注意，使用 ASCII 文字名稱並不保證跨應用程式保存檔案的唯一性。 因此，您應該標記資料檔案，以避免損毀。 在插入類別資訊之後，封存會將物件放入*m_pStoreMap* ，然後呼叫 `Serialize` 方法來插入類別特定的資料。 在 `Serialize` 呼叫之前將物件放入*m_pStoreMap* ，可防止將物件的多個複本儲存到存放區。

當返回初始呼叫端（通常是物件的網路的根）時，您必須呼叫[CArchive：： Close](../mfc/reference/carchive-class.md#close)。 如果您打算執行其他[CFile](../mfc/reference/cfile-class.md)作業，您必須呼叫 `CArchive` 方法[Flush](../mfc/reference/carchive-class.md#flush) ，以避免封存損毀。

> [!NOTE]
>  針對每個封存內容，此實作為0x3FFFFFFE 索引的固定限制。 這個數位代表唯一物件和類別的最大數目，可以儲存在單一封存中，但是單一磁片檔案可以有不限數量的封存內容。

## <a name="loading-objects-from-the-store-carchivereadobject"></a>從存放區載入物件（CArchive：： ReadObject）

載入（解壓縮）物件會使用 `CArchive::ReadObject` 方法，而且是 `WriteObject`的反向。 如同 `WriteObject`，不會直接由使用者程式碼呼叫 `ReadObject`。使用者程式碼應呼叫型別安全的抽取運算子，以使用預期的 `CRuntimeClass`呼叫 `ReadObject`。 這會確保解壓縮作業的類型完整性。

因為 `WriteObject` 的實值已指派增加的 Pid，從1開始（0已預先定義為 Null 物件），所以 `ReadObject` 執行可以使用陣列來維護封存內容的狀態。 從存放區讀取 PID 時，如果 PID 大於*m_pLoadArray*的目前上限，`ReadObject` 知道新的物件（或類別描述）如下所示。

## <a name="schema-numbers"></a>架構編號

當遇到類別的 `IMPLEMENT_SERIAL` 方法時，會指派給類別的架構編號，是類別執行的「版本」。 架構是指類別的實值，而不是指定之物件的持續時間（通常稱為物件版本）。

如果您想要在一段時間內維護數個相同類別的不同實作為，當您修改物件的 `Serialize` 方法執行時，就會遞增架構，讓您可以撰寫程式碼，以便載入使用舊版執行所儲存的物件。

當 `CArchive::ReadObject` 方法在持續性存放區中遇到與記憶體中類別描述的架構編號不同的架構編號時，將會擲回[CArchiveException](../mfc/reference/carchiveexception-class.md) 。 從這個例外狀況中復原並不容易。

您可以使用 `VERSIONABLE_SCHEMA` 結合（位**或**）您的架構版本，以防止擲回此例外狀況。 藉由使用 `VERSIONABLE_SCHEMA`，您的程式碼可以從[CArchive：： GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)檢查傳回值，以在其 `Serialize` 函數中採取適當的動作。

## <a name="calling-serialize-directly"></a>直接呼叫序列化

在許多情況下，`WriteObject` 和 `ReadObject` 一般物件封存配置的負擔並不是必要的。 這是將資料序列化為[CDocument](../mfc/reference/cdocument-class.md)的常見案例。 在此情況下，會直接呼叫 `CDocument` 的 `Serialize` 方法，而不是使用「抽取」或「插入」運算子。 檔的內容可能會轉而使用較一般的物件封存配置。

直接呼叫 `Serialize` 具有下列優點和缺點：

- 在物件序列化之前或之後，不會將額外的位元組新增至封存。 這不僅可讓儲存的資料變小，還可讓您執行可處理任何檔案格式的 `Serialize` 常式。

- MFC 經過微調，因此除非您需要更一般的物件封存配置以供其他用途，否則 `WriteObject` 和 `ReadObject` 的執行和相關的集合將不會連結到您的應用程式。

- 您的程式碼不需要從舊的架構編號復原。 這會讓您的檔序列化程式碼負責編碼架構數位、檔案格式版本號碼，或您在資料檔開頭使用的任何識別數位。

- 任何以直接呼叫 `Serialize` 序列化的物件都不能使用 `CArchive::GetObjectSchema` 或必須處理傳回值（UINT）-1，表示版本不明。

因為 `Serialize` 是直接在您的檔上呼叫，所以檔的子物件通常不可能將參考封存到其父檔。 這些物件必須明確地提供其容器檔案的指標，或者您必須使用[CArchive：： MapObject](../mfc/reference/carchive-class.md#mapobject)函式，將 `CDocument` 指標對應到 PID，才會封存這些後置指標。

如先前所述，當您直接呼叫 `Serialize` 時，您應該自行編碼版本和類別資訊，讓您稍後可以變更格式，同時仍維持與舊版檔案的回溯相容性。 在直接序列化物件之前或呼叫基類之前，可以明確呼叫 `CArchive::SerializeClass` 函數。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
