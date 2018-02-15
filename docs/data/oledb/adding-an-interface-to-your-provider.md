---
title: "將介面加入至您的提供者 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 518cd5e67c734de48d7f021e558c7c4c3a718cdc
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="adding-an-interface-to-your-provider"></a>將介面加入至提供者
決定您想要將介面加入 （通常是資料來源、 資料列集、 命令或工作階段物件 OLE DB 提供者精靈所建立） 的物件。 很可能您要加入至介面的物件是目前不支援您的提供者的其中一個。 在此情況下，執行 ATL OLE DB 提供者精靈來建立物件。 以滑鼠右鍵按一下 類別檢視中的專案中，按一下**加入類別**從**新增**功能表，然後再按一下**ATL OLE DB 提供者**。 您可能想要放在個別的目錄中的介面程式碼，然後將檔案複製到提供者專案。  
  
 如果您建立新的類別，以支援介面，請繼承自該類別的物件。 例如，您可以在其中加入類別**IRowsetIndexImpl**資料列集物件：  
  
```cpp  
template <class Creator>  
class CAgentRowset :   
    public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
    public IRowsetIndexImpl< ... >   
```  
  
 加入至介面**COM_MAP**使用 COM_INTERFACE_ENTRY 巨集在物件中。 如果沒有對應，建立一個。 例如:   
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
 資料列集物件，鏈結其父代的對應物件，讓物件可以委派給父類別。 在此範例中，加入對應 COM_INTERFACE_ENTRY_CHAIN 巨集：  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## <a name="see-also"></a>請參閱  
 [使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)