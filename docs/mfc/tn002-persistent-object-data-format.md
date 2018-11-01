---
title: TN002：持續性物件資料格式
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 5f5bde68d9fd4175ed97a7b61d807887d07e9e12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474382"
---
# <a name="tn002-persistent-object-data-format"></a>TN002：持續性物件資料格式

此提示描述 MFC 常式，它支援持續性的 c + + 物件和物件資料的格式，儲存在檔案中時。 這只適用於具有類別[DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial)並[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)巨集。

## <a name="the-problem"></a>問題

永續性資料的 MFC 實作會將許多物件的資料儲存在單一連續的檔案部分。 物件的`Serialize`方法會將物件的資料轉譯壓縮的二進位格式。

實作可保證所有的資料會儲存在相同的格式，利用[CArchive 類別](../mfc/reference/carchive-class.md)。 它會使用`CArchive`成為翻譯工具的物件。 這個物件仍然存在，直到您呼叫，它會建立時間[CArchive::Close](../mfc/reference/carchive-class.md#close)。 呼叫這個方法可以由程式設計師明確或隱含的解構函式時結束範圍包含程式`CArchive`。

本提示描述實作`CArchive`成員[CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject)並[CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject)。 您會找到 Arcobj.cpp，主要適用於和實作中這些函式的程式碼`CArchive`Arccore.cpp 中。 使用者程式碼不會呼叫`ReadObject`和`WriteObject`直接。 相反地，這些物件會使用特定類別的型別安全插入和擷取運算子會自動產生的 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 巨集。 下列程式碼示範如何`WriteObject`和`ReadObject`隱含地呼叫：

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>將物件儲存至存放區 (CArchive::WriteObject)

此方法`CArchive::WriteObject`寫入用來重建物件的標頭資料。 這項資料是由兩個部分所組成： 物件類型和物件的狀態。 這個方法也會負責維護的寫入位置，該物件的身分識別，以便儲存單一複本，不論該物件 （包括循環的指標） 指標的數目。

儲存 （插入），並還原 （解壓縮） 物件依賴數個 「 資訊清單常數 」。 以下是會儲存在二進位檔，並提供重要資訊以封存 （請注意"w"前置詞表示 16 位元數量） 的值：

|標記|描述|
|---------|-----------------|
|wNullTag|使用 NULL 物件指標 (0)。|
|wNewClassTag|指出此封存內容 (-1) 的新類別描述所示。|
|wOldClassTag|表示正在讀取之物件的類別，曾在此內容 (0x8000)。|

封存儲存時的物件，會維護[CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( *m_pStoreMap*) 這是從預存物件對應至 32 位元持續性識別碼 (PID)。 PID 會指派給每個唯一物件和儲存在封存的內容中的每個唯一的類別名稱。 這些 Pid 發出以循序方式從 1 開始。 這些 Pid 封存的範圍外有沒有意義，而且，特別是，要不會與記錄的數字或其他識別項目混淆。

在 `CArchive`類別，Pid 為 32 位元，但它們會寫出做為 16 位元不大於 0x7FFE。 大型的 Pid 會寫為 0x7FFF 後面接著 32 位元 PID。 這會維護與較早的版本中所建立的專案相容性。

若要封存至儲存的物件 （通常是藉由使用全域插入運算子） 提出要求時的 null 值進行檢查[CObject](../mfc/reference/cobject-class.md)指標。 如果指標為 NULL， *wNullTag*插入封存資料流。

如果指標不是 NULL，且可序列化 (此類別是`DECLARE_SERIAL`類別)，程式碼會檢查*m_pStoreMap*以查看是否有已儲存物件。 如果有，程式碼會插入到封存資料流，與該物件相關聯的 32 位元 PID。

如果物件尚未儲存之前，有兩個要考慮的可能性： 物件和物件的確切類型 （也就是類別） 不熟悉此封存內容中，或是物件是已經看過的確實型別。 若要判斷是否所見的型別，程式碼會查詢*m_pStoreMap*的[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)符合物件`CRuntimeClass`所儲存的物件相關聯的物件。 如果沒有相符項目，`WriteObject`插入的標記，是位元`OR`的*wOldClassTag*和此索引。 如果`CRuntimeClass`是此封存內容中，新增`WriteObject`會指派至該類別的新 PID，並將它插入到封存，前面加上*wNewClassTag*值。

這個類別的描述項會插入封存使用`CRuntimeClass::Store`方法。 `CRuntimeClass::Store` 插入結構描述數目的類別 （如下所示） 和類別的 ASCII 文字名稱。 請注意，使用 ASCII 文字名稱並不保證唯一性的封存跨應用程式。 因此，您應該標記您的資料檔案，以避免損毀。 下列類別資訊插入，封存會將物件放入*m_pStoreMap* ，然後呼叫`Serialize`插入類別的特定資料的方法。 將物件插入*m_pStoreMap*再呼叫`Serialize`防止物件的多個複本儲存至存放區。

在傳回給初始呼叫者 （通常是根物件的網路） 時，您必須呼叫[CArchive::Close](../mfc/reference/carchive-class.md#close)。 如果您打算執行其他[CFile](../mfc/reference/cfile-class.md)作業，您必須呼叫`CArchive`方法[排清](../mfc/reference/carchive-class.md#flush)以避免損毀的封存檔。

> [!NOTE]
>  這項實作硬限制 0x3FFFFFFE 索引，每個保存內容。 這個數字代表唯一的物件和類別可以在單一保存，儲存的最大數目，但單一磁碟檔案可以有無限的數量的封存內容。

## <a name="loading-objects-from-the-store-carchivereadobject"></a>從存放區 (CArchive::ReadObject) 載入物件

正在載入 （擷取） 物件會使用`CArchive::ReadObject`方法，且反向`WriteObject`。 如同`WriteObject`，`ReadObject`不直接由使用者程式碼呼叫使用者程式碼應該呼叫型別安全擷取運算子會呼叫`ReadObject`與預期`CRuntimeClass`。 這樣可確保在擷取作業類型的完整性。

由於`WriteObject`實作指派增加的 Pid，從 1 開始 （0 預先定義為 NULL 的物件），`ReadObject`實作可以使用陣列來維護封存內容的狀態。 PID 讀取時從存放區中，如果 PID 為大於目前上限*m_pLoadArray*，`ReadObject`知道，新的物件 （或類別描述） 如下所示。

## <a name="schema-numbers"></a>結構描述的數字

結構描述編號，這指派給類別時`IMPLEMENT_SERIAL`類別的方法時，是在類別實作 「 版本 」。 結構描述是指類別的實作，不必次數指定的物件發出永續性 （通常稱為 「 物件版本 」）。

如果您想要維護一段時間的相同類別的數個不同的實作，遞增結構描述當您修改您的物件`Serialize`方法實作可讓您撰寫程式碼，可以載入儲存使用舊版物件實作。

`CArchive::ReadObject`方法會擲回[CArchiveException](../mfc/reference/carchiveexception-class.md)當它遇到結構描述中的數字和類別描述在記憶體中結構描述數目不同的持續性存放區。 您不容易從這個例外狀況中復原。

您可以使用`VERSIONABLE_SCHEMA`結合 (位元**或**) 結構描述版本將擲回這個例外狀況。 藉由使用`VERSIONABLE_SCHEMA`，您的程式碼可以採取適當的動作，其`Serialize`藉由檢查傳回值的函式[CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)。

## <a name="calling-serialize-directly"></a>呼叫直接序列化

在許多情況下的一般物件封存配置的額外負荷`WriteObject`和`ReadObject`不需要。 這是常見的案例的序列化資料載入[CDocument](../mfc/reference/cdocument-class.md)。 在此情況下，`Serialize`方法的`CDocument`直接被呼叫，不會與擷取或插入運算子。 文件的內容可能會接著使用較為普遍的物件保存配置。

呼叫`Serialize`直接具有下列優點和缺點：

- 任何額外的位元組會不新增至封存之前或之後將物件序列化。 這不只可儲存的資料較小，但可讓您實作`Serialize`常式可以處理任何檔案格式。

- MFC 會調整因此`WriteObject`和`ReadObject`實作和相關的集合將不會連結到您的應用程式除非您需要更一般的物件保存配置供其他用途。

- 您的程式碼並沒有復原從舊的結構描述數字。 這可讓您的文件序列化程式碼負責編碼結構描述的數字、 檔案格式版本號碼，或任何用來識別數字開頭的資料檔案使用。

- 任何物件，會以直接呼叫序列化`Serialize`不能使用`CArchive::GetObjectSchema`或必須控制代碼 (UINT)-1 的傳回值，指出版本不明。

因為`Serialize`稱為直接在文件時，就無法通常要封存至其父代文件的參考文件的子物件。 這些物件必須獲指定一個指標至其容器文件明確，或者您必須使用[CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject)函式對應`CDocument`PID 之前要封存這些反向指標的指標。

如先前所述，您應該編碼版本和類別資訊自行呼叫時`Serialize`直接，讓您可以稍後變更格式，同時仍維持回溯相容性的較舊的檔案。 `CArchive::SerializeClass`之前直接序列化物件或之前先呼叫基底類別函式也可以明確地呼叫。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

