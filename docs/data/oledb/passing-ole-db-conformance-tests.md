---
title: 通過 OLE DB 一致性測試
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: f7c5435003866e2c3490bd07e28ec10eca0ec0cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491711"
---
# <a name="passing-ole-db-conformance-tests"></a>通過 OLE DB 一致性測試

若要讓提供者更一致，Data Access SDK 會提供一組 OLE DB 一致性測試。 測試會檢查您的提供者的所有層面，並讓您合理的保證，讓您的提供者函式，做為預期。 您可以在 Microsoft Data Access SDK 中找到 OLE DB 一致性測試。 本節著重於事您應該將一致性測試。 如需執行 OLE DB 一致性測試的資訊，請參閱 SDK。

## <a name="running-the-conformance-tests"></a>執行一致性測試

在 Visual c + + 6.0 中，OLE DB 提供者範本會加入可讓您檢查值和屬性的攔截函式數目。 大部分的這些函式已加入一致性測試的回應。

> [!NOTE]
> 您要新增您的提供者，將 OLE DB 一致性測試的數個驗證函式。

此提供者需要兩個驗證常式。 第一個常式， `CRowsetImpl::ValidateCommandID`，是您的資料列集類別的一部分。 它會呼叫在資料列集建立期間提供者樣板。 此範例會使用這個常式，以告知取用者不支援索引。 第一個呼叫是對`CRowsetImpl::ValidateCommandID`(提供者所使用的附註`_RowsetBaseClass`新增的介面對應中的 typedef`CCustomRowset`中[書籤的提供者支援](../../data/oledb/provider-support-for-bookmarks.md)，因此您不需要輸入該範本的較長的行引數）。 接下來，如果索引參數不是 NULL，傳回 DB_E_NOINDEX （這表示取用者想要使用的索引，我們的產品）。 如需有關命令 Id 的詳細資訊，請參閱 OLE DB 規格，並尋找`IOpenRowset::OpenRowset`。

下列程式碼是`ValidateCommandID`驗證常式：

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

提供者範本呼叫`OnPropertyChanged`每當有人在變更屬性的方法`DBPROPSET_ROWSET`群組。 如果您想要處理的其他群組的屬性，您將它們加入適當的物件 (亦即`DBPROPSET_SESSION`檢查進入`CCustomSession`類別)。

程式碼會先檢查是否要將屬性連結至另一個。 如果屬性要鏈結，它會設定`DBPROP_BOOKMARKS`屬性設`True`。 OLE DB 規格的附錄 C 包含內容的相關資訊。 這項資訊也會告訴您是否將屬性鏈結至另一個。

您也可以在新增`IsValidValue`常式程式碼。 範本呼叫`IsValidValue`時嘗試設定屬性。 如果您需要額外的處理設定的屬性值時，會覆寫這個方法。 您可以其中一種方法，每個屬性集。

## <a name="see-also"></a>另請參閱

[進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)