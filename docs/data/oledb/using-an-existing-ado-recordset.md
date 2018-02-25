---
title: "使用現有的 ADO 資料錄集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a819a0f292951060f4dc6b9fdda580db8f0d2127
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)