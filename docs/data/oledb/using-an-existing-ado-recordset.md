---
title: 使用現有的 ADO 資料錄集
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 62e56b818a766bf3b7efddf9243ffd47ad2cb46f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610596"
---
# <a name="using-an-existing-ado-recordset"></a>使用現有的 ADO 資料錄集

若要混合使用 OLE DB 消費者範本和 Active Data Objects (ADO)、 使用 ADO 開啟資料錄集 （相當於 OLE DB 消費者樣板中的資料列集）。 當您有一個資料錄集時，執行下列命令來連接到 OLE DB 資料列集：

1. 呼叫`QueryInterface`for`IRowset`和`IAccessor`指標。

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk*指向`IUnknown`ADO 資料錄集物件。

1. 附加至其適當的 OLE DB 消費者範本類別的存取子和資料列集。

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)