---
title: 將介面加入至提供者
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: 295a7955b78918d6281a28b616f201869f37b01e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488669"
---
# <a name="adding-an-interface-to-your-provider"></a>將介面加入至提供者

決定您想要將介面新增至 （通常是資料來源、 資料列集、 命令或工作階段物件 OLE DB 提供者精靈所建立） 的物件。 很可能您要加入至介面的物件是您的提供者目前不支援的其中一個。 在此情況下，執行 ATL OLE DB 提供者精靈來建立物件。 以滑鼠右鍵按一下 [類別檢視] 中的專案中，按一下**加入類別**從**新增**功能表，然後再按一下**ATL OLE DB 提供者**。 您可能想要的介面程式碼置於個別的目錄，然後將檔案複製到您的提供者專案。

如果您建立新的類別，以支援介面，請繼承自該類別的物件。 例如，您可以在其中加入類別**IRowsetIndexImpl**資料列集物件：

```cpp
template <class Creator>
class CAgentRowset :
    public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,
    public IRowsetIndexImpl< ... >
```

加入至介面**COM_MAP**使用 COM_INTERFACE_ENTRY 巨集之物件中。 如果沒有任何對應，請建立一個。 例如: 

```cpp
BEGIN_COM_MAP(CAgentRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

資料列集物件的鏈結其父代的對應物件，讓物件可以委派給父類別。 在此範例中，加入對應 COM_INTERFACE_ENTRY_CHAIN 巨集：

```cpp
BEGIN_COM_MAP(CAgentRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)