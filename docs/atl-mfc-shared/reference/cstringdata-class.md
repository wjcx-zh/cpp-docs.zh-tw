---
title: "CStringData Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStringData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringData class"
  - "shared classes, CStringData"
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# CStringData Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示字串物件的資料。  
  
## 語法  
  
```  
  
struct CStringData  
  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[AddRef](../Topic/CStringData::AddRef.md)|將字串資料物件的參考計數。|  
|[data](../Topic/CStringData::data.md)|擷取字串物件的字元資料。|  
|[IsLocked](../Topic/CStringData::IsLocked.md)|判斷關聯字串物件的緩衝區是否已鎖定。|  
|[IsShared](../Topic/CStringData::IsShared.md)|判斷關聯字串物件的緩衝區目前是否為共用。|  
|[鎖定](../Topic/CStringData::Lock.md)|鎖定關聯字串物件的緩衝區。|  
|[Release](../Topic/CStringData::Release.md)|釋放指定的字串物件。|  
|[解除鎖定](../Topic/CStringData::Unlock.md)|開啟關聯字串物件的緩衝區。|  
  
### 資料成員  
  
|||  
|-|-|  
|[nAllocLength](../Topic/CStringData::nAllocLength.md)|配置之資料的長度 \(以 `XCHAR`s 的 \(不包含結尾 null\)|  
|[nDataLength](../Topic/CStringData::nDataLength.md)|在 `XCHAR`s 的目前所使用之資料的長度 \(包括 null 終止\)|  
|[nRefs](../Topic/CStringData::nRefs.md)|目前物件的參考計數。|  
|[pStringMgr](../Topic/CStringData::pStringMgr.md)|將這個字串物件的資料處理常式之的指標。|  
  
## 備註  
 應該是實作自訂字串處理常式的開發人員只使用此類別。  如需自訂字串處理常式的詳細資訊，請參閱 [記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 這個類別會封裝資訊的各種類型，而資料與較高的字串物件，例如、或 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) 物件。  每個較高的字串物件含有指向其關聯的 `CStringData` 物件，允許對多點的字串物件為相同的字串資料物件。  此關聯性可由參考計數 \(`nRefs`\) 表示 `CStringData` 物件。  
  
> [!NOTE]
>  在某些案例中，資料型別 \(例如\) **CFixedString**擁有超過一個以上的字串物件不會共用資料的資料物件。  如需詳細資訊，請參閱 [記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
 這項資料所組成:  
  
-   記憶體管理員 \(屬於型別 [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)\) 的字串。  
  
-   目前長度 \([nDataLength](../Topic/CStringData::nDataLength.md)\) 的字串。  
  
-   配置的長度 \([nAllocLength](../Topic/CStringData::nAllocLength.md)\) 的字串。  基於效能考量，這可以與目前的長度不同。  
  
-   目前參考計數 \([nRefs](../Topic/CStringData::nRefs.md)\) `CStringData` 物件。  這個值用於判斷字串物件共用相同的 `CStringData` 物件。  
  
-   實際字元緩衝區 \([資料](../Topic/CStringData::data.md)\) 字串。  
  
    > [!NOTE]
    >  字串處理常式配置字串物件的實際字元緩衝區和附加至 `CStringData` 物件。  
  
## 需求  
 **Header:** atlsimpstr.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)