---
title: "CObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基底類別, MFC 物件"
  - "CObject class"
  - "object classes"
  - "物件 [C++], base class for MFC"
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 程式庫之主要基底類別。  
  
## 語法  
  
```  
class AFX_NOVTABLE CObject  
```  
  
## 成員  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CObject::CObject](../Topic/CObject::CObject.md)|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CObject::AssertValid](../Topic/CObject::AssertValid.md)|驗證這個物件的完整性。|  
|[CObject::Dump](../Topic/CObject::Dump.md)|導致此物件的診斷傾印。|  
|[CObject::GetRuntimeClass](../Topic/CObject::GetRuntimeClass.md)|傳回 `CRuntimeClass` 結構與這個物件類別對應。|  
|[CObject::IsKindOf](../Topic/CObject::IsKindOf.md)|測試是否為特定類別的這個物件的關聯性。|  
|[CObject::IsSerializable](../Topic/CObject::IsSerializable.md)|測試以查看這個物件進行序列化。|  
|[CObject::Serialize](../Topic/CObject::Serialize.md)|載入或儲存物件從\/拖曳至檔案。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CObject::operator delete](../Topic/CObject::operator%20delete.md)|特殊 **刪除** 運算子。|  
|[CObject::operator new](../Topic/CObject::operator%20new.md)|特殊 **new** 運算子。|  
  
## 備註  
 它會影響不僅程式庫類別的 `CFile``CObList`，例如和，也會儲存於所撰寫的類別。  `CObject` 提供基本服務，包括  
  
-   支援序列化。  
  
-   執行階段類別資訊  
  
-   物件診斷輸出。  
  
-   與集合類別的相容性  
  
 請注意 `CObject` 不支援多重繼承。  您的衍生類別只能有一個 `CObject` 基底類別，因此，該 `CObject` 必須位於最左側在階層架構。  是可允許的，不過，結構和非`CObject`\-在右方多重繼承分支的衍生類別。  
  
 如果在類別實作和宣告，使用一些選擇性巨集就會知道從 `CObject` 衍生的主要優點。  
  
 第一層的巨集、 [DECLARE\_DYNAMIC](../Topic/DECLARE_DYNAMIC.md) 和 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md)、允許執行階段存取類別名稱和位置以階層架構。  這個方法，接著，允許有意義診斷傾印。  
  
 第二層巨集， [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) 和 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md)，包括第一層的巨集的所有功能，，而且可以讓物件「與「file」序列化」。  
  
 如需一般購買 Microsoft Foundation Classes 和 C\+\+ 類別和使用 `CObject`的詳細資訊，請參閱 [使用 CObject](../../mfc/using-cobject.md) 和 [序列化](../../mfc/serialization-in-mfc.md)。  
  
## 繼承階層架構  
 `CObject`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)