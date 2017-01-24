---
title: "使用現有的 ADO 資料錄集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ADO 資料錄集 [C++]"
  - "OLE DB 消費者樣板, ADO 資料錄集"
  - "資料錄集 [C++], 使用於 OLE DB"
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用現有的 ADO 資料錄集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要混合使用 OLE DB 消費者樣板和 Active Data Object \(ADO\)，請使用 ADO 開啟資料錄集 \(對應至 OLE DB 消費者樣板中的資料列集\)。  當您擁有資料錄集時，請執行下列動作以連接至 OLE DB 資料列集：  
  
1.  呼叫 `QueryInterface` 來取得 `IRowset` 和 `IAccessor` 指標。  
  
    ```  
    IRowset* lpRowset = NULL;  
    IAccessor* lpAccessor = NULL;  
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);  
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);  
    ```  
  
    > [!NOTE]
    >  *lpUnk* 會指向 ADO 資料錄集的 **IUnknown** 物件。  
  
2.  將存取子和資料列集附加到其適用的 OLE DB 消費者樣板類別 \(Template Class\)。  
  
    ```  
    CRowset rs;  
    CAccessor accessor;  
  
    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor  
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>  
    rs.SetAccessor(accessor);  
    ```  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)