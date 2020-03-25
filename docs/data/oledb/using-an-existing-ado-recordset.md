---
title: 使用現有的 ADO 資料錄集
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 48f6eb3bac34b37f495b9492e19b4197ed69cca3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209348"
---
# <a name="using-an-existing-ado-recordset"></a>使用現有的 ADO 資料錄集

若要混合 OLE DB 取用者範本和 Active Data Objects （ADO），請使用 ADO 開啟記錄集（對應至 OLE DB 取用者範本中的資料列集）。 當您擁有記錄集時，請執行下列動作來連接到 OLE DB 的資料列集：

1. 呼叫 `IRowset` 和 `IAccessor` 指標的 `QueryInterface`。

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk*會指向 ADO 記錄集的 `IUnknown` 物件。

1. 將存取子和資料列集附加至適當的 OLE DB 取用者範本類別。

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)
