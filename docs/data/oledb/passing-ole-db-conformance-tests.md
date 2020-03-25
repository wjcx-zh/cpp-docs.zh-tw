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
ms.openlocfilehash: eda4dccda147ddd4776bb56e649f539a7550abd1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209759"
---
# <a name="passing-ole-db-conformance-tests"></a>通過 OLE DB 一致性測試

為了使提供者更一致，資料存取 SDK 會提供一組 OLE DB 的一致性測試。 測試會檢查提供者的所有層面，並讓您能夠合理地保證您的提供者如預期般運作。 您可以在 Microsoft Data Access SDK 上找到 OLE DB 的一致性測試。 本節著重于傳遞合規性測試時應採取的動作。 如需執行 OLE DB 一致性測試的相關資訊，請參閱 SDK。

## <a name="running-the-conformance-tests"></a>執行一致性測試

在 Visual C++ 6.0 中，OLE DB 提供者範本加入了一些連結功能，可讓您檢查值和屬性。 這些函式大部分都是為了回應一致性測試而新增的。

> [!NOTE]
> 您需要為您的提供者新增數個驗證函式，以傳遞 OLE DB 的一致性測試。

此提供者需要兩個驗證常式。 第一個常式（`CRowsetImpl::ValidateCommandID`）是資料列集類別的一部分。 在提供者範本建立資料列集時，會呼叫它。 此範例會使用此常式來告訴取用者它不支援索引。 第一次呼叫是 `CRowsetImpl::ValidateCommandID` （請注意，提供者會使用在介面對應中新增的 `_RowsetBaseClass` typedef `CCustomRowset` 來[提供支援的書簽](../../data/oledb/provider-support-for-bookmarks.md)，因此您不需要輸入該長行範本引數）。 接下來，如果索引參數不是 Null，則傳回 DB_E_NOINDEX （這表示取用者想要使用我們的索引）。 如需有關命令識別碼的詳細資訊，請參閱 OLE DB 規格並尋找 `IOpenRowset::OpenRowset`。

下列程式碼是 `ValidateCommandID` 驗證常式：

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

每當有人變更 DBPROPSET_ROWSET 群組的屬性時，提供者範本就會呼叫 `OnPropertyChanged` 方法。 如果您想要處理其他群組的屬性，請將它們新增至適當的物件（也就是 DBPROPSET_SESSION 檢查 `CCustomSession` 類別中的 [移至]）。

程式碼會先檢查屬性是否連結至另一個。 如果屬性正在進行連鎖，它會將 DBPROP_BOOKMARKS 屬性設為 `True`。 OLE DB 規格的附錄 C 包含屬性的相關資訊。 這項資訊也會告訴您屬性是否連結至另一個。

您可能也會想要將 `IsValidValue` 常式新增至程式碼。 當您嘗試設定屬性時，範本會呼叫 `IsValidValue`。 如果您在設定屬性值時需要額外的處理，則會覆寫這個方法。 您可以為每個屬性集設定其中一種方法。

## <a name="see-also"></a>另請參閱

[進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)
