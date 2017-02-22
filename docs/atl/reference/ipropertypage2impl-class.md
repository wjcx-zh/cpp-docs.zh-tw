---
title: "IPropertyPage2Impl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPropertyPage2Impl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPropertyPage2 ATL implementation"
  - "IPropertyPage2Impl class"
  - "屬性頁"
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IPropertyPage2Impl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 和繼承 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的預設實作。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template< class   
      T  
      >  
class IPropertyPage2Impl : public IPropertyPageImpl< T>  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IPropertyPage2Impl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IPropertyPage2Impl::EditProperty](../Topic/IPropertyPage2Impl::EditProperty.md)|指定哪個屬性控制項將接收焦點，在屬性頁中啟動。  ATL 實作會傳回 **E\_NOTIMPL**。|  
  
## 備註  
 [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) 介面會加入 `EditProperty` 方法擴充 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) 。  這個方法允許用戶端選取  屬性頁上物件的特定屬性。  
  
 類別 `IPropertyPage2Impl` 傳回 **IPropertyPage2::EditProperty**的 **E\_NOTIMPL** 。  不過，它繼承 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) 的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 當您建立屬性頁時，您的類別繼承 `IPropertyPageImpl`通常衍生自類別。  若要提供 **IPropertyPage2**額外的支援，請修改您的類別定義 `EditProperty` 並覆寫方法。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IPropertyPage`  
  
 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [IPerPropertyBrowsingImpl Class](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl Class](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)