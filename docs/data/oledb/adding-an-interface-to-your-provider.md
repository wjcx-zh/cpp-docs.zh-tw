---
title: 將介面加入至提供者
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: c0452ca74509b65de3787af93bff41b3cb399c99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384968"
---
# <a name="adding-an-interface-to-your-provider"></a>將介面加入至提供者

判斷哪個物件您想要新增至介面 (通常由建立資料來源、 資料列集、 命令或工作階段物件**OLE DB 提供者精靈**)。 很可能您要加入至介面的物件是您的提供者目前不支援的其中一個。 在此情況下，執行**ATL OLE DB 提供者精靈**來建立物件。 中的專案上按一下滑鼠右鍵**類別檢視**，按一下**新增** > **新項目**從功能表中選取**安裝** > **視覺化C++**   >  **ATL**，然後按一下**ATL OLEDB 提供者**。 您可能想要的介面程式碼置於個別的目錄，然後將檔案複製到您的提供者專案。

如果您建立新的類別，以支援介面，請繼承自該類別的物件。 例如，您可以在其中加入類別`IRowsetIndexImpl`資料列集物件：

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

加入 COM_MAP 的介面中使用 COM_INTERFACE_ENTRY 巨集的物件。 如果沒有任何對應，請建立一個。 例如: 

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

資料列集物件的鏈結其父代的對應物件，讓物件可以委派給父類別。 在此範例中，加入對應 COM_INTERFACE_ENTRY_CHAIN 巨集：

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)