---
title: "CComEnumOnSTL Class | Microsoft Docs"
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
  - "CComEnumOnSTL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComEnumOnSTL class"
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComEnumOnSTL Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會定義以 STL 集合的 COM 列舉值物件。  
  
## 語法  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy,  
   class CollType,  
   class ThreadModel = CComObjectThreadModel  
>  
class ATL_NO_VTABLE CComEnumOnSTL :  
   public IEnumOnSTLImpl<Base, piid, T, Copy, CollType>,  
   public CComObjectRootEx< ThreadModel >  
```  
  
#### 參數  
 `Base`  
 COM 列舉值 \([IEnumXXXX](https://msdn.microsoft.com/en-us/library/ms680089.aspx)\) 介面。  
  
 `piid`  
 out 列舉值介面的介面 ID 的指標。  
  
 `T`  
 列舉值介面公開的項目型別。  
  
 `Copy`  
 [複製原則](../../atl/atl-copy-policy-classes.md) 類別。  
  
 `CollType`  
 STL 容器類別。  
  
## 備註  
 `CComEnumOnSTL` 定義根據 STL 集合的 COM 列舉值物件。  這個類別可單獨使用或 [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)一起使用。  的一般步驟。使用這個類別會在中說明。  如需詳細資訊，請參閱 [ATL 集合和列舉值。](../../atl/atl-collections-and-enumerators.md)。  
  
## 使用 ICollectionOnSTLImpl 中這個類別:  
  
-   `typedef` 此類別的特製化。  
  
-   使用 `typedef` 做為最終的樣板引數在 `ICollectionOnSTLImpl`的特製化。  
  
 如需範例 [ATL 集合和列舉值。](../../atl/atl-collections-and-enumerators.md) 參閱。  
  
## 獨立 ICollectionOnSTLImpl 使用這個類別:  
  
-   `typedef` 此類別的特製化。  
  
-   使用 `typedef` 當做樣板引數使用。 `CComObject`的特製化。  
  
-   建立 `CComObject` 特製化的執行個體。  
  
-   藉由呼叫 [IEnumOnSTLImpl::Init](../Topic/IEnumOnSTLImpl::Init.md)初始化列舉值物件。  
  
-   傳回列舉值介面給用戶端。  
  
## 繼承階層架構  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## 需求  
 **Header:** atlcom.h  
  
## 範例  
 下面所示的程式碼提供泛型函式處理列舉值物件的建立和初始化:  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/CPP/ccomenumonstl-class_1.h)]  
  
 這個樣板函式可用來實作介面的集合 `_NewEnum` 屬性如下所示:  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/CPP/ccomenumonstl-class_2.h)]  
  
 藉由 **IEnumVariant** 介面公開 `CComVariant`s 向量的這個程式碼會建立 `CComEnumOnSTL` 的 `typedef` 。  **CVariantCollection** 類別特製化 **CreateSTLEnumerator** 與型別搭配使用列舉值物件。  
  
## 請參閱  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [ATLCollections 範例:示範 ICollectionOnSTLImpl、CComEnumOnSTL 和自訂複製原則類別](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md)   
 [IEnumOnSTLImpl Class](../../atl/reference/ienumonstlimpl-class.md)