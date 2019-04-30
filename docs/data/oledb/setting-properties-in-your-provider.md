---
title: 在提供者內設定屬性
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 2cbb334ab15912fdcf6980461016976d869f5a84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404503"
---
# <a name="setting-properties-in-your-provider"></a>在提供者內設定屬性

尋找您想要的屬性的屬性群組和屬性識別碼。 如需詳細資訊，請參閱 < [OLE DB 屬性](/previous-versions/windows/desktop/ms722734(v=vs.85))中**OLE DB 程式設計人員參考**。

在精靈產生的提供者程式碼的情況下，找到對應至屬性群組的屬性對應。 屬性群組的名稱通常會對應到物件的名稱。 命令和資料列集屬性可在命令或資料列集;資料來源物件中可以找到資料來源初始化屬性。

在 屬性對應，新增[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)巨集。 PROPERTY_INFO_ENTRY_EX 接受四個參數：

- 屬性 ID 對應至您的屬性。 從屬性名稱的前面移除的前七個字元 ("DBPROP_ 」)。 例如，如果您想要新增`DBPROP_MAXROWS`，傳遞`MAXROWS`的第一個元素。 如果這是自訂的屬性，傳遞完整的 GUID 名稱 (例如`DBMYPROP_MYPROPERTY`)。

- 屬性的 variant 型別 (在[OLE DB 屬性](/previous-versions/windows/desktop/ms722734(v=vs.85))中**OLE DB 程式設計人員參考**)。 輸入 VT_ 類型 （例如 VT_BOOL 或 VT_I2） 對應到資料類型。

- 加上旗標以指出屬性是否可讀取和寫入，且其所屬的群組。 例如，下列程式碼表示屬於資料列群組的讀取/寫入屬性：

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- 屬性的基底值。 這可能是`VARIANT_FALSE`布林類型，或零的整數類型，例如。 屬性會有此值，除非它已被變更。

    > [!NOTE]
    > 連接或鏈結至其他屬性，例如書籤或更新某些屬性。 當取用者會將一個屬性設定為 true 時，也可以設定其他屬性。 OLE DB 提供者範本則會透過方法支援這[cutlprops:: Onpropertychanged](../../data/oledb/cutlprops-onpropertychanged.md)。

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Microsoft OLE DB 提供者所忽略的屬性

Microsoft OLE DB 提供者會忽略下列的 OLE DB 屬性：

- `DBPROP_MAXROWS` 僅適用於唯讀提供者 (也就是`DBPROP_IRowsetChange`並`DBPROP_IRowsetUpdate`會**false**); 否則不支援這個屬性。

- `DBPROP_MAXPENDINGROWS` 會忽略;提供者會指定它自己的限制。

- `DBPROP_MAXOPENROWS` 會忽略;提供者會指定它自己的限制。

- `DBPROP_CANHOLDROWS` 會忽略;提供者會指定它自己的限制。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)