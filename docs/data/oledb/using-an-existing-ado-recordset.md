---
title: 使用現有的 ADO 資料錄集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 36c74ec0d17c296707334930736d0cf237ecfe7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103560"
---
# <a name="using-an-existing-ado-recordset"></a>使用現有的 ADO 資料錄集
混合 OLE DB 消費者樣板和作用中 Data Objects (ADO)，使用 ADO 來開啟資料錄集 （OLE DB 消費者樣板中的資料列集對應）。 當您有一個資料錄集時，執行下列命令來連接到 OLE DB 資料列集：  
  
1.  呼叫`QueryInterface`如`IRowset`和`IAccessor`指標。  
  
    ```  
    IRowset* lpRowset = NULL;  
    IAccessor* lpAccessor = NULL;  
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);  
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);  
    ```  
  
    > [!NOTE]
    >  *lpUnk*指向**IUnknown** ADO 資料錄集的物件。  
  
2.  附加至其適當的 OLE DB 消費者樣板類別的存取子和資料列集。  
  
    ```  
    CRowset rs;  
    CAccessor accessor;  
  
    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor  
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>  
    rs.SetAccessor(accessor);  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)