---
title: "ISpecifyPropertyPagesImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ISpecifyPropertyPagesImpl"
  - "ATL.ISpecifyPropertyPagesImpl<T>"
  - "ATL::ISpecifyPropertyPagesImpl"
  - "ATL::ISpecifyPropertyPagesImpl<T>"
  - "ATL.ISpecifyPropertyPagesImpl"
  - "ISpecifyPropertyPagesImpl Class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISpecifyPropertyPages"
  - "ISpecifyPropertyPagesImpl class"
  - "屬性頁, CLSIDs associated with"
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ISpecifyPropertyPagesImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 並提供 [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) 介面的預設實作。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl :  
public ISpecifyPropertyPages  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `ISpecifyPropertyPagesImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[ISpecifyPropertyPagesImpl::GetPages](../Topic/ISpecifyPropertyPagesImpl::GetPages.md)|填滿封閉的 UUID 值。  每個 UUID 對應於物件的屬性工作表中顯示的其中一個的 CLSID 屬性頁。|  
  
## 備註  
 [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) 介面可讓用戶端取得物件所支援的屬性頁的 CLSID 的清單。  類別 `ISpecifyPropertyPagesImpl` 提供這個介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
> [!NOTE]
>  此外，如果您的物件不支援屬性頁，請不要公開 **ISpecifyPropertyPages** 介面。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [IPropertyPageImpl Class](../../atl/reference/ipropertypageimpl-class.md)   
 [IPerPropertyBrowsingImpl Class](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)