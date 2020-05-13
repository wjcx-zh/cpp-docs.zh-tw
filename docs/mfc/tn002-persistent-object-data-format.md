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
ms.openlocfilehash: f65a7b7afcf6bd832c9c23560bb29374038fae1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370447"
---
# <a name="tn002-persistent-object-data-format"></a>TN002：持續性物件資料格式

本註釋介紹支援持久C++物件的MFC例程,以及對象數據存儲在檔中時的格式。 這僅適用於具有[DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)宏的類。

## <a name="the-problem"></a>問題

持久數據的 MFC 實現將許多物件的數據存儲在檔的單個連續部分。 物件`Serialize`的方法將對象的數據轉換為緊湊的二進位格式。

實現保證透過使用[CArchive 類](../mfc/reference/carchive-class.md)以相同的格式保存所有數據。 它使用`CArchive`物件作為轉換器。 此物件從建立時一直持續到呼叫[CArchive::關閉](../mfc/reference/carchive-class.md#close)。 當程式退出包含的範圍時,程式師可以顯式調用此方法,也可以由析構函數隱式調用`CArchive`此方法。

本說明描述了`CArchive`成員[CArchive::讀取物件](../mfc/reference/carchive-class.md#readobject)和[CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject)的實現。 您可以在 Arcobj.cpp 中找到這些函數的代碼,以及 Arccore.cpp`CArchive`中的主要實現。 用戶代碼不直接調用`ReadObject`和`WriteObject`調用。 相反,這些物件由特定於類的類型安全插入和提取運算符使用,這些運算符由DECLARE_SERIAL和IMPLEMENT_SERIAL宏自動生成。 以下代碼顯示如何`WriteObject``ReadObject`與隱式呼叫:

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>儲存物件儲存到儲存(CArchive::寫入物件)

該方法`CArchive::WriteObject`寫入用於重建對象的標頭數據。 此數據由兩部分組成:對象的類型和物件的狀態。 此方法還負責維護正在寫入的對象的標識,以便只保存單個副本,而不考慮指向該物件的指標數(包括迴圈指標)。

保存(插入)和還原(提取)對象依賴於多個"清單常量"。 這些值以二進位方式存儲,並且向存檔提供重要資訊(請注意,"w"前綴表示 16 位元數量):

|Tag|描述|
|---------|-----------------|
|wNullTag|用於 NULL 物件指標 (0)。|
|wNewClassTag|指示後面的類描述是此存檔上下文 (-1) 的新增內容說明。|
|wOldClassTag|指示在此上下文中 (0x8000) 已看到正在讀取的物件的類。|

儲存物件時,存檔維護一個[CMapPtrToPtr(m_pStoreMap),](../mfc/reference/cmapptrtoptr-class.md)它是從儲存的物件映射到 32 位元持久標識碼*m_pStoreMap*(PID)。 PID 分配給保存在存檔上下文中的每個唯一物件和每個唯一類名稱。 這些 PID 從 1 開始按順序分發。 這些 PID 在存檔範圍之外沒有意義,尤其不應與記錄編號或其他標識項混淆。

在類`CArchive`中,PID 是 32 位,但它們被寫成 16 位元,除非它們大於 0x7FFE。 大型 PID 編寫為 0x7FFF,後跟 32 位 PID。 這將保持與在早期版本中創建的專案的相容性。

當請求將物件保存到存檔時(通常使用全域插入運算子),將檢查 NULL [CObject](../mfc/reference/cobject-class.md)指標。 如果指標為 NULL,則*wNullTag*將插入到存檔流中。

如果指標不是 NULL 並且可以序列化(類`DECLARE_SERIAL`是 類),則代碼將檢查*m_pStoreMap*以查看物件是否已保存。 如果有,代碼將與該物件關聯的 32 位 PID 插入到存檔流中。

如果物件以前未保存,則有兩種可能性需要考慮:對象和對象的確切類型(即類)都是此存檔上下文的新類型,或者對像是已看到的確切類型。 要確定是否已看到該類型,代碼會查詢與要保存`CRuntimeClass`的物件關聯的物件的[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)物件的*m_pStoreMap。* 如果存在匹配項,則`WriteObject`插入*wOldClassTag*和此索引的`OR`位標記。 如果`CRuntimeClass`是此存檔上下文的新增`WriteObject`, 請向該類分配新的 PID 並將其插入到存檔中,前面是*wNewClassTag*值。

然後,使用方法`CRuntimeClass::Store`將此類的描述符插入到存檔中。 `CRuntimeClass::Store`插入類的架構編號(見下文)和類的 ASCII 文本名稱。 請注意,使用 ASCII 文本名稱並不保證整個應用程式存檔的唯一性。 因此,您應該標記數據檔以防止損壞。 插入類資訊後,存檔將物件放入*m_pStoreMap,* 然後`Serialize`調用 方法插入特定於類的數據。 在調用`Serialize`之前將物件放入*m_pStoreMap*可防止將物件的多個副本保存到存儲中。

傳回到初始呼叫者(通常是物件網路的根),必須呼叫[CArchive::關閉](../mfc/reference/carchive-class.md#close)。 如果計劃執行其他[CFile](../mfc/reference/cfile-class.md)操作,則必須`CArchive`呼叫[「刷新」](../mfc/reference/carchive-class.md#flush)方法以防止存檔損壞。

> [!NOTE]
> 此實現對每個存檔上下文的 0x3FFFFE 索引施加了硬限制。 此數位表示可保存在單個存檔中的最大唯一物件和類數,但單個磁碟檔可以具有無限數量的存檔上下文。

## <a name="loading-objects-from-the-store-carchivereadobject"></a>從儲存載入物件(CArchive::讀取物件)

載入(擷取)物件使用`CArchive::ReadObject`方法 ,`WriteObject`與相反 。 與`WriteObject``ReadObject`一樣,用戶代碼不直接調用 ;使用者代碼應調用`ReadObject`使用預期`CRuntimeClass`的類型安全提取運算符。 這將確保數據提取操作的類型完整性。

由於`WriteObject`分配的實現不斷增加 PID,從 1 開始(0 預定義為 NULL 物件),實現`ReadObject`可以使用陣列來維護存檔上下文的狀態。 從儲存中讀取 PID 時,如果 PID 大於`ReadObject`*m_pLoadArray*的當前上限, 則知道將遵循新物件(或類描述)。

## <a name="schema-numbers"></a>架構編號

遇到類`IMPLEMENT_SERIAL`的方法時分配給類的架構編號是類實現的"版本"。 架構是指類的實現,而不是給定物件被持久化的次數(通常稱為物件版本)。

如果打算隨著時間的推移維護同一類的幾個不同實現,則在修改物件`Serialize`的方法實現時增加架構將使您能夠編寫代碼,這些代碼可以使用舊版本的實現載入存儲的物件。

`CArchive::ReadObject`當該方法在持久存儲中遇到與記憶體中類描述的架構編號不同的架構編號時,將引發[CArchiveException。](../mfc/reference/carchiveexception-class.md) 要從此異常中恢復並不容易。

您可以使用`VERSIONABLE_SCHEMA`( 位**元或**) 架構版本來防止引發此異常。 通過使用`VERSIONABLE_SCHEMA`,您的代碼可以`Serialize`通過檢查[CArchive::getObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)中的返回值來在其函數中採取適當的操作。

## <a name="calling-serialize-directly"></a>直接呼叫序列化

在許多情況下,一般物件存檔方案的開銷`WriteObject``ReadObject`是沒有必要的。 這是將數據序列化到[CDocument](../mfc/reference/cdocument-class.md)的常見情況。 在這種情況下,`Serialize`直接調用`CDocument`的方法 ,而不是使用提取或插入運算符調用。 文檔的內容可能反過來使用更通用的物件存檔方案。

直接`Serialize`調用有以下優點和缺點:

- 在物件序列化之前或之後,不會向存檔添加額外的位元組。 這不僅使保存的數據變小,還允許您實現`Serialize`可以處理任何檔案格式的例程。

- MFC 已調整,`WriteObject`因此`ReadObject`, 除非出於其他目的需要更通用的物件存檔方案,否則不會將和實現和相關集合連結到您的應用程式中。

- 您的代碼不必從舊的架構編號中恢復。 這使文件序列化代碼負責對架構碼、檔案格式版本號或數據檔開頭使用的任何標識編號進行編碼。

- 使用直接呼叫序列化的任何物件`Serialize`不得`CArchive::GetObjectSchema`使用 或必須處理 (UINT)-1 的返回值,指示版本未知。

由於`Serialize`直接在文件上調用,因此文檔的子物件通常無法存檔對其父文檔的引用。 必須顯式為這些物件提供指向其容器文件的指標,否則您必須使用[CArchive:mapObject](../mfc/reference/carchive-class.md#mapobject)函數將`CDocument`這些指標映射到 PID,然後才能存檔這些回指標。

如前所述,在直接調用`Serialize`時,應自行對版本和類資訊進行編碼,以便以後更改格式,同時仍與舊檔保持向後相容性。 可以直接`CArchive::SerializeClass`序列化物件之前或調用基類之前,可以顯式調用該函數。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
