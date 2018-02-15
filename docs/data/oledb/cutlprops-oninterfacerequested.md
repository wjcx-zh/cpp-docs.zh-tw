---
title: "Cutlprops:: Oninterfacerequested |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps
dev_langs:
- C++
helpviewer_keywords:
- OnInterfaceRequested method
ms.assetid: a5e1a879-cff3-4e01-b902-2249a152984f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eb15d2574ba60dcec9c0638ca10a465db5813709
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cutlpropsoninterfacerequested"></a>CUtlProps::OnInterfaceRequested
當取用者呼叫方法的其中一個物件建立介面來處理要求的選擇性的介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
      virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 [in]所要求介面的 IID。 如需詳細資訊，請參閱描述`riid`參數`ICommand::Execute`中*OLE DB 程式設計人員參考*(在*MDAC SDK*)。  
  
## <a name="remarks"></a>備註  
 **OnInterfaceRequested**處理取用者要求選擇性的介面，當取用者呼叫方法的其中一個物件建立介面 (例如**IDBCreateSession**， **IDBCreateCommand**， `IOpenRowset`，或`ICommand`)。 它會設定對應的 OLE DB 屬性所要求介面。 例如，如果取用者要求**IID_IRowsetLocate**， **OnInterfaceRequested**設定**DBPROP_IRowsetLocate**介面。 這樣會維護正確的狀態資料列集建立期間。  
  
 當取用者呼叫時，會呼叫這個方法**iopenrowset:: Openrowset**或`ICommand::Execute`。  
  
 如果取用者會開啟物件，並要求選擇性的介面，提供者應該將該介面，相關聯的屬性`VARIANT_TRUE`。 若要允許內容特定處理**OnInterfaceRequested**的提供者之前，會呼叫**Execute**方法呼叫。 根據預設， **OnInterfaceRequested**處理下列介面：  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   **IConnectionPointContainer**  
  
-   `IRowsetScroll`  
  
 如果您想要處理其他介面，覆寫這個函式在資料來源、 工作階段、 命令或資料列集類別到處理程序函式中。 覆寫應透過一般 set/get 屬性介面，以確保，設定屬性也會設定任何鏈結的內容 (請參閱[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md))。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)