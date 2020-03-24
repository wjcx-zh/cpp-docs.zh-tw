---
title: 在提供者內設定屬性
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 905a9bb32544dbd7453d46362e100047516d22a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209569"
---
# <a name="setting-properties-in-your-provider"></a>在提供者內設定屬性

尋找您想要之屬性的屬性群組和屬性 ID。 如需詳細資訊，請參閱 OLE DB 程式設計**人員參考**中的[OLE DB 屬性](/previous-versions/windows/desktop/ms722734(v=vs.85))。

在嚮導所產生的提供者程式碼中，尋找對應至屬性群組的 [屬性對應]。 屬性群組的名稱通常會對應至物件的名稱。 命令和資料列集屬性可以在命令或資料列集中找到;資料來源和初始化屬性可以在資料來源物件中找到。

在屬性對應中，加入[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)宏。 PROPERTY_INFO_ENTRY_EX 採用四個參數：

- 對應至您的屬性的屬性識別碼。 從屬性名稱的前面移除前七個字元（"DBPROP_"）。 例如，如果您想要加入 `DBPROP_MAXROWS`，請傳遞 `MAXROWS` 做為第一個元素。 如果這是自訂屬性，請傳遞完整的 GUID 名稱（例如，`DBMYPROP_MYPROPERTY`）。

- 屬性的 variant 類型（在 OLE DB 程式設計**人員參考**的[OLE DB 屬性](/previous-versions/windows/desktop/ms722734(v=vs.85))中）。 輸入對應至資料類型的 VT_ 類型（例如 VT_BOOL 或 VT_I2）。

- 旗標，指出屬性是否為可讀取和可寫入，以及它所屬的群組。 例如，下列程式碼表示屬於資料列集群組的讀取/寫入屬性：

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- 屬性的基底值。 這可能是布林值類型的 `VARIANT_FALSE`，或整數類型的零（例如）。 屬性具有此值，除非它已變更。

    > [!NOTE]
    > 某些屬性會連接或連結至其他屬性，例如書簽或更新。 當取用者將一個屬性設定為 true 時，也可能會設定另一個屬性。 OLE DB 提供者範本透過[CUtlProps：： OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)方法來支援此動作。

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Microsoft OLE DB 提供者忽略的屬性

Microsoft OLE DB 提供者會忽略下列 OLE DB 屬性：

- `DBPROP_MAXROWS` 僅適用于唯讀提供者（也就是，其中 `DBPROP_IRowsetChange` 和 `DBPROP_IRowsetUpdate` 為**false**）;否則不支援這個屬性。

- 已忽略 `DBPROP_MAXPENDINGROWS`;提供者會指定自己的限制。

- 已忽略 `DBPROP_MAXOPENROWS`;提供者會指定自己的限制。

- 已忽略 `DBPROP_CANHOLDROWS`;提供者會指定自己的限制。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)
