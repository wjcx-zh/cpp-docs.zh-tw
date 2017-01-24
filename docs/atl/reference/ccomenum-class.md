---
title: "CComEnum Class | Microsoft Docs"
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
  - "CComEnum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComEnum class"
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComEnum Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會定義以陣列的 COM 列舉值物件。  
  
## 語法  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy,  
   class ThreadModel = CcomObjectThreadModel  
>  
class ATL_NO_VTABLE CComEnum :  
   public CComEnumImpl<Base, piid, T, Copy>,  
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
 同質性 [複製原則類別](../../atl/atl-copy-policy-classes.md)。  
  
 `ThreadModel`  
 類別的執行緒模型。  這個參數會預設為用於專案的全域物件執行緒模型。  
  
## 備註  
 `CComEnum` 定義根據陣列的 COM 列舉值物件。  實作以 STL 容器的列舉值的這個類別 \(Class\) 類似 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) 。  的一般步驟。使用這個類別會在中說明。  如需詳細資訊，請參閱 [ATL 集合和列舉值。](../../atl/atl-collections-and-enumerators.md)。  
  
## 使用這個類別:  
  
-   `typedef` 此類別的特製化。  
  
-   使用 `typedef` 當做樣板引數使用。 `CComObject`的特製化。  
  
-   建立 `CComObject` 特製化的執行個體。  
  
-   藉由呼叫 [CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md)初始化列舉值物件。  
  
-   傳回列舉值介面給用戶端。  
  
## 繼承階層架構  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)  
  
 `CComEnum`  
  
## 需求  
 **Header:** atlcom.h  
  
## 範例  
 如下所示的程式碼會建立和初始化列舉值物件提供可重複使用的函式。  
  
 [!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/CPP/ccomenum-class_1.h)]  
  
 這個樣板函式可用來實作介面的集合 `_NewEnum` 屬性如下所示:  
  
 [!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/CPP/ccomenum-class_2.h)]  
  
 藉由 **IEnumVariant** 介面公開 **VARIANT**s 向量的這個程式碼會建立 `CComEnum` 的 `typedef` 。  **CVariantArrayCollection** 類別特製化 **CreateEnumerator** 與型別搭配使用列舉值物件並將必要的引數。  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md)   
 [CComEnumImpl Class](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)