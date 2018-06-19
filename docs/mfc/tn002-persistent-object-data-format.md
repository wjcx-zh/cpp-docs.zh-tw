---
title: TN002： 持續性物件資料格式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca145ff871e1c5ccff27bdebe473c6cb6f39073a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385413"
---
# <a name="tn002-persistent-object-data-format"></a>TN002：持續性物件資料格式
此提示描述支援持續性的 c + + 物件和物件資料的格式，它會儲存在檔案中的 MFC 常式。 這只適用於具有類別[DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)巨集。  
  
## <a name="the-problem"></a>問題  
 永續性資料的 MFC 實作會將許多物件的資料儲存在單一連續的檔案部分。 物件的`Serialize`方法將物件的資料轉譯成壓縮的二進位格式。  
  
 實作可保證所有的資料會儲存在相同的格式，使用[CArchive 類別](../mfc/reference/carchive-class.md)。 它會使用`CArchive`當做轉譯程式的物件。 此物件持續發生，直到您呼叫建立的時間從[CArchive::Close](../mfc/reference/carchive-class.md#close)。 呼叫這個方法可以由程式設計人員明確或隱含的解構函式在程式結束所包含的範圍時`CArchive`。  
  
 此提示描述實作`CArchive`成員[CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject)和[CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject)。 您將找到的程式碼中 Arcobj.cpp，以及主要實作這些函式`CArchive`Arccore.cpp 中。 使用者程式碼不會呼叫`ReadObject`和`WriteObject`直接。 相反地，這些物件由類別的特定型別安全插入和擷取運算子所自動產生`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`巨集。 下列程式碼示範如何`WriteObject`和`ReadObject`隱含地呼叫：  
  
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
  
## <a name="saving-objects-to-the-store-carchivewriteobject"></a>將物件儲存到存放區 (CArchive::WriteObject)  
 此方法`CArchive::WriteObject`寫入標頭用來重建物件的資料。 這項資料是由兩個部分所組成： 物件類型和物件的狀態。 這個方法也會負責維護，正在寫入物件的識別，以便儲存單一複本時，不論該物件 （包括循環的指標） 的指標的數目。  
  
 儲存 （插入），並還原 （解壓縮） 物件依賴數個 「 資訊清單常數。 」 這些是儲存在二進位檔，並提供重要資訊以封存 （請注意"w"前置詞表示 16 位元數量） 的值：  
  
|標記|描述|  
|---------|-----------------|  
|wNullTag|使用 NULL 物件指標 (0)。|  
|wNewClassTag|表示此封存內容 (-1) 的新類別描述所示。|  
|wOldClassTag|表示正在讀取的物件類別發生過此內容 (0x8000)。|  
  
 當儲存物件，封存會維護[CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( `m_pStoreMap`) 即從預存物件對應至 32 位元持續性識別項 (PID)。 PID 為指派給每個唯一的物件和儲存在封存的內容中每個唯一類別名稱。 這些 Pid 發出以循序方式從 1 開始。 這些 Pid 已封存的範圍外不重要，而且特別是，要與記錄的數字或其他識別項目混淆。  
  
 在`CArchive`類別，Pid 為 32 位元，但它們會寫出做為 16 位元除非大於 0x7FFE。 大型 Pid 將寫成 0x7FFF 後面接著 32 位元 PID。 這樣會維護與舊版中所建立的專案的相容性。  
  
 若要封存儲存物件 （通常是使用全域插入運算子） 提出要求時的 null 值進行檢查[CObject](../mfc/reference/cobject-class.md)指標。 如果指標為 NULL，`wNullTag`插入至封存資料流。  
  
 如果指標不是 NULL，而可序列化 (此類別是`DECLARE_SERIAL`類別)，程式碼檢查`m_pStoreMap`以查看是否物件已儲存。 如果是，程式碼會插入到封存資料流，與該物件相關聯的 32 位元 PID。  
  
 如果物件尚未儲存之前，有兩種可能性，考慮： 物件和物件的確切類型 （也就是類別） 新增到此封存內容，或是物件屬於已經看過的確切類型。 若要判斷是否曾發生型別，程式碼查詢`m_pStoreMap`如[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)符合物件`CRuntimeClass`所儲存物件相關聯的物件。 如果沒有相符項目，`WriteObject`插入之標記的位元`OR`的`wOldClassTag`和此索引。 如果`CRuntimeClass`是此封存內容中，新`WriteObject`將指派給該類別的新 PID，並將它封存，前面加上插入`wNewClassTag`值。  
  
 這個類別的描述元會插入封存使用`CRuntimeClass::Store`方法。 `CRuntimeClass::Store` 插入結構描述編號 （請參閱下文） 的類別和類別的 ASCII 文字名稱。 請注意使用 ASCII 文字名稱並不保證唯一性的封存跨應用程式。 因此，您應該標記您的資料檔案，以避免損毀。 下列類別資訊插入，封存會將物件放入`m_pStoreMap`，然後呼叫`Serialize`方法插入類別的特定資料。 將物件插入`m_pStoreMap`之前先呼叫`Serialize`防止多個物件的複本儲存至存放區。  
  
 傳回至初始呼叫者 （通常是根物件的網路） 時，您必須呼叫[CArchive::Close](../mfc/reference/carchive-class.md#close)。 如果您打算執行其他[CFile](../mfc/reference/cfile-class.md)作業，您必須呼叫`CArchive`方法[排清](../mfc/reference/carchive-class.md#flush)以避免保存檔損毀。  
  
> [!NOTE]
>  此實作會加諸的固定限制的每個保存內容 0x3FFFFFFE 索引。 這個數字代表唯一物件和類別，可以在單一保存，儲存的最大數目，但單一磁碟檔案可以有無限的數量的封存內容。  
  
## <a name="loading-objects-from-the-store-carchivereadobject"></a>從存放區 (CArchive::ReadObject) 載入物件  
 載入 （擷取） 物件使用`CArchive::ReadObject`方法的反向而且`WriteObject`。 如同`WriteObject`，`ReadObject`不直接由使用者程式碼; 呼叫使用者程式碼應該會呼叫型別安全擷取運算子呼叫`ReadObject`與需要`CRuntimeClass`。 這樣可確保複本擷取作業的類型的完整性。  
  
 因為`WriteObject`實作指派增加的 Pid，從 1 開始 （0 預先定義為 NULL 物件），`ReadObject`實作可以使用陣列維護封存內容的狀態。 PID 讀取時從存放區中，如果超過目前上限的 PID `m_pLoadArray`，`ReadObject`知道，新的物件 （或類別描述） 如下所示。  
  
## <a name="schema-numbers"></a>結構描述的數字  
 結構描述編號，指派至類別時`IMPLEMENT_SERIAL`類別的方法時，是在類別實作 「 版本 」。 結構描述參考類別的實作時，不必次數指定的物件發出持續性 （通常稱為物件版本）。  
  
 如果您想要維護一段時間的數個不同的相同類別實作時，遞增結構描述修改您的物件為`Serialize`方法實作可讓您撰寫程式碼，可以載入儲存使用的舊版本的物件實作。  
  
 `CArchive::ReadObject`方法會擲回[CArchiveException](../mfc/reference/carchiveexception-class.md)當它遇到類別描述在記憶體中結構描述數目不同的持續性存放區中的結構描述編號。 它並不容易從這個例外狀況復原。  
  
 您可以使用`VERSIONABLE_SCHEMA`結合 (位元`OR`) 您的結構描述版本，將擲回這個例外狀況。 使用`VERSIONABLE_SCHEMA`，程式碼會採取適當的動作，其`Serialize`函式，藉由檢查傳回的值從[CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)。  
  
## <a name="calling-serialize-directly"></a>呼叫直接序列化  
 在許多情況下的一般物件封存配置的額外負荷`WriteObject`和`ReadObject`不需要。 這是常見的序列化資料的情況[CDocument](../mfc/reference/cdocument-class.md)。 在此情況下，`Serialize`方法`CDocument`直接被呼叫，不能搭配擷取或插入運算子。 文件的內容可能會接著會使用更一般的物件封存配置。  
  
 呼叫`Serialize`直接具有下列優點和缺點：  
  
-   任何額外的位元組會不加入到封存之前或之後將物件序列化。 這不只會儲存的資料較小，但可讓您實作`Serialize`常式可以處理任何檔案格式。  
  
-   MFC 也都能得到微調所以`WriteObject`和`ReadObject`實作和相關的集合將不會連結到您的應用程式除非您需要更一般的物件保存配置供其他用途。  
  
-   您的程式碼並沒有復原從舊的結構描述數字。 這可讓您的文件序列化程式碼負責編碼結構描述的數字、 檔案格式版本號碼，或任何識別數字開頭的資料檔案使用。  
  
-   任何直接呼叫序列化的物件`Serialize`不得使用`CArchive::GetObjectSchema`或必須控制代碼 (UINT)-1 的傳回值，指出版本不明。  
  
 因為`Serialize`稱為直接在文件時，就不通常可能要封存其父代文件的參考文件的子物件。 這些物件必須提供指標給其容器文件明確，或者您必須使用[CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject)函式對應`CDocument`PID 之前會保存這些的上一頁指標的指標。  
  
 如前文所述，您應該編碼版本和類別資訊自行呼叫時`Serialize`直接管理，讓您可以稍後變更格式，同時仍維持回溯相容性的較舊的檔案。 `CArchive::SerializeClass`之前直接序列化物件或之前呼叫的基底類別函式也可以明確地呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

