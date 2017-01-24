---
title: "CComTearOffObject Class | Microsoft Docs"
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
  - "ATL::CComTearOffObject<Base>"
  - "ATL::CComTearOffObject"
  - "ATL.CComTearOffObject"
  - "ATL.CComTearOffObject<Base>"
  - "CComTearOffObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComTearOffObject class"
  - "tear-off interfaces"
  - "tear-off interfaces, ATL"
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComTearOffObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 Tear\-Off 介面。  
  
## 語法  
  
```  
  
      template<  
   class Base   
>  
class CComTearOffObject :  
   public Base  
```  
  
#### 參數  
 `Base`  
 請 Tear\-Off 類別，衍生自 `CComTearOffObjectBase` ，而您希望 Tear\-Off 為支援介面的物件。  
  
 ATL 是以兩個階段實作它自己 Tear\-Off 介面— `CComTearOffObjectBase` 方法處理參考計數和 `QueryInterface`，反之， `CComTearOffObject` 實作 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComTearOffObject::CComTearOffObject](../Topic/CComTearOffObject::CComTearOffObject.md)|建構函式。|  
|[CComTearOffObject::~CComTearOffObject](../Topic/CComTearOffObject::~CComTearOffObject.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComTearOffObject::AddRef](../Topic/CComTearOffObject::AddRef.md)|將 `CComTearOffObject` 物件的參考計數。|  
|[CComTearOffObject::QueryInterface](../Topic/CComTearOffObject::QueryInterface.md)|傳回指向儲存在您 Tear\-Off 類別或擁有者類別的要求的介面。|  
|[CComTearOffObject::Release](../Topic/CComTearOffObject::Release.md)|會 `CComTearOffObject` 物件的參考次數並終止。|  
  
### CComTearOffObjectBase 方法  
  
|||  
|-|-|  
|[CComTearOffObjectBase](../Topic/CComTearOffObject::CComTearOffObjectBase.md)|建構函式。|  
  
### CComTearOffObjectBase 資料成員  
  
|||  
|-|-|  
|[m\_pOwner](../Topic/CComTearOffObject::m_pOwner.md)|為 `CComObject` 的指標從主控類別衍生自。|  
  
## 備註  
 `CComTearOffObject` Tear\-Off 實作介面，因為具現化的物件，但該介面進行查詢。  其參考計數為零時， Tear\-Off 刪除。  通常，您會建立很少使用介面的介面， Tear\-Off，因為使用 Tear\-Off 儲存在您的主要物件的所有執行個體的 vtable 指標。  
  
 您應該從 `CComTearOffObjectBase` Tear\-Off 實作衍生自的類別中，並從介面想要請 Tear\-Off 為支援的物件。  在`CComTearOffObjectBase` 擁有者類別和執行緒模型樣板化。  擁有者類別為 Tear\-Off 實作物件的類別。  如果您沒有指定執行緒模型，使用預設執行緒模型。  
  
 您必須建置 COM 對應 Tear\-Off 類別。  在 ATL Tear\-Off 具現化，它會建立 **CComTearOffObject\<CYourTearOffClass\>** 或 **CComCachedTearOffObject\<CYourTearOffClass\>**。  
  
 例如，在 BEEPER 範例， `CBeeper2` 類別為 Tear\-Off 類別，並 `CBeeper` 類別是擁有人類別:  
  
 [!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/CPP/ccomtearoffobject-class_1.h)]  
  
## 繼承階層架構  
 `Base`  
  
 `CComTearOffObject`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComCachedTearOffObject Class](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)