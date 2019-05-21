---
title: 將介面加入至提供者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: a1d219568c1787558674c47edd55436b8690a61c
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524799"
---
# <a name="adding-an-interface-to-your-provider"></a>將介面加入至提供者

> [!NOTE]
> Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。

判斷您想要將介面加入至哪一個物件 (通常是由 **OLE DB 提供者精靈**所建立的資料來源、資料列集、命令或工作階段物件)。 您需要將介面加入至其中的物件很可能是您的提供者目前不支援的物件。 在此情況下，請執行 **ATL OLE DB 提供者精靈**來建立該物件。 在 [類別檢視] 中以滑鼠右鍵按一下專案、從功能表中按一下 [加入] > [新的項目]、選取 [安裝] > [Visual C++] > [ATL]，然後按一下 [ATL OLEDB 提供者]。 您可能想要將介面程式碼放入不同目錄，然後將檔案複製到您的提供者專案。

如果您建立新類別來支援介面，則必須使物件繼承自該類別。 例如，您可以將類別 `IRowsetIndexImpl` 加入至資料列集物件：

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

使用 COM_INTERFACE_ENTRY 巨集，將介面加入至物件中的 COM_MAP。 如果沒有任何對應，請建立一個。 例如：

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

針對資料列集物件，鏈結其父物件的對應，如此一來，物件就能委派給父類別。 在此範例中，將 COM_INTERFACE_ENTRY_CHAIN 巨集加入至對應：

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)