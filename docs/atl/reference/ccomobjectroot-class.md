---
title: "CComObjectRoot Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComObjectRoot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectRoot class"
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectRoot Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) typedef 伺服器上的預設執行緒模型樣板化。  
  
## 語法  
  
```  
  
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;  
  
```  
  
## 備註  
 `CComObjectRoot` 是 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)`typedef` 樣板化伺服器上的預設執行緒模型。  因此 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 會參考 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) 或 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。  
  
 `CComObjectRootEx` 控制代碼物件參考 nonaggregated 和彙總物件的計數管理。  它會保留物件的參考次數，如果物件不可彙總，並保有指標至外部 UNKNOWN，如果您物件的彙總。  對於彙總物件， `CComObjectRootEx` 方法可用來處理內部物件的失敗\] 建構的，因此，保護外部物件遭刪除，而放開內部介面或內部物件刪除。  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComObjectRootEx Class Members](http://msdn.microsoft.com/zh-tw/e3ce9c3d-9c8e-4fe5-b682-8e56740a0164)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)